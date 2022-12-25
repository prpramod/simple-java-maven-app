pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -Denforcer.skip=true -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn -Denforcer.skip=true test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
        stage('Complete') {
            steps {
                echo 'staging Job completed'
            }
        }
    }
}
