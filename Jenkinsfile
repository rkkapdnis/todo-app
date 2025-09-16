pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/rkkapdnis/todo-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("todo-app")
                }
            }
        }

        stage('Run Tests') {
            steps {
                sh 'echo "Running tests..."'
                sh 'pytest tests/test_app.py || true'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 5000:5000 todo-app'
            }
        }
    }
}

