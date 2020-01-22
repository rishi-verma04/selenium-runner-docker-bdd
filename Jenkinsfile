pipeline{
    agent any
    stages{
        stage("Pull Latest Image"){
            steps{
                sh "docker pull rishiyudi04/selenium-docker-bdd"
            }
        }
        stage("Start Grid"){
            steps{
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run Test"){
            steps{
                sh "docker-compose up "
            }
        }
    }
    post{
        always{
            archiveArtifacts artifacts: 'output/**'
            sh "docker-compose down"
            sh "sudo rm -rf output/"
        }
    }
}