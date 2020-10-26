pipeline {
    agent any
    stages {
        stage('BuildNew') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('TestNew') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('DeliverNew') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
