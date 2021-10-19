 pipeline {
  agent {
      docker{
          image 'maven:3-alpine'
          args '-v/root/.m2:/root/.m2'
      }
    
  }
    stages {
        stage('Build') {
            steps {
                echo 'Cleaning..'
                bat 'mvn -B -DskipTests clean'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                bat 'mvn test'
            }
             post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        stage('Delivery') {
            steps {
                
                bat './jenkins/scripts/deliver.bat'
            }
           
        }

        
    }
}
