@Library('gitlib')_
pipeline{
    agent { label 'slave-1'}
    
    stages{
        stage("Code clone"){
            steps{

            clone("https://github.com/sanjaybdch9/node-todo-cicd.git","master")
            }
        }
        stage("Code Build")
        {
            steps{
            dockerbuild("notes-app","latest")
            }
        }
        stage("Push to DockerHub"){
            steps{
                push("dockerHubCreds","notes-app","latest")
            }
        }
        stage("Compose"){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
        }
        
    }
}

