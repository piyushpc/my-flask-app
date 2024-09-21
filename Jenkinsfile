pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'master', url: 'https://github.com/piyushpc/my-flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("my-flask-app")
                }
            }
        }

        stage('Test') {
            steps {
                sh 'docker run my-flask-app pytest'  # Run tests inside Docker container
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh 'kubectl apply -f k8s/deployment.yaml'  # Assuming we have a deployment.yaml for Kubernetes
            }
        }
    }
}
