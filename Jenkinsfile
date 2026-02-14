@Library("shared") _
pipeline{
    agent { label "pratham" }
    
        stages{
            
            stage("Hello"){
                steps{
                    script{
                        hello()
                    }
                }
            }
            
            stage("code"){
                steps{
                    script{
                    clone("https://github.com/LondheShubham153/django-notes-app.git","dev")
                }
            }
        }
            
            stage("build"){
                steps{
                   script{
                    docker_build("notes-app","latest","prathamsharma12")
                }
            }
        }
            stage("Push to dockerhub"){
                 steps{
                   script{
                       docker_push("notes-app","latest")
                   }
                }
            }
            
            stage("deploy"){
                steps{
                    echo "this is deploying the code"
                    sh "docker compose down && compose up -d"
                    echo "notes-app successfully deployed"
                }
           }
     }
}
