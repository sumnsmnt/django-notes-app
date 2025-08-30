@Library("shared") _
pipeline{
    agent any
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/sumnsmnt/django-notes-app.git", "main")
                }
            }
        }
        
        stage("Build"){
             steps{
                script{
                    docker_build("notes-app", "latest", "sumnsmnt99")
                }
            }           
        }
        
        stage("Test"){
             steps{
                echo "This is for testing the Code"
            }           
        }
        
         stage("Push to DockerHub"){
             steps{
                script{
                    docker_push("notes-app", "latest", "sumnsmnt99")
                }
            }           
        }
               
        
        stage("Deploy"){
              steps{
                echo "This is for deploying the Code"
                sh 'docker compose down && docker compose up -d --build'

            }          
        }
    }
}
