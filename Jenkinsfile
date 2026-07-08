pipeline {

    agent any

    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/username/student-devops-app.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t student-app:v1 .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f student-container || true
                docker run -d --name student-container student-app:v1
                '''
            }
        }

    }
}
