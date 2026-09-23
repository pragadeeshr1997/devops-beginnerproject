pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                echo 'Source code already checked out by Jenkins'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build --no-cache -t myapp:latest .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f myapp || true

                docker run -d \
                --name myapp \
                -p 8081:80 \
                myapp:latest
                '''
            }
        }
    }
}
