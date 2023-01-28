pipeline {
    agent any
    stages {
        stage('Clone The Repository') {
            steps {
                git 'https://github.com/rajshamz/letsquiz.git'
            }
        }
        stage('Build Docker Container') {
            steps {
                script {
                    def app = docker.build("quizapp:latest", ".")
                }
            }
        }
        stage('Deploy to Docker Desktop') {
            steps {
                script {
                    sh 'docker stop quizapp || true'
                    sh 'docker rm quizapp || true'
                    sh 'docker run --name quizapp -d -p 8099:80 quizapp:latest'
                }
            }
        }
    }
}
