pipeline {
    agent any
 
    stages {
        stage("checkout") {
            steps {
                echo "Checkout the code from GitHub"
                git url: "https://github.com/satya918/helloworld.git/", branch: "main"
            }
        }
        stage ('Build') {
            steps {
              
                sh 'mvn clean package'
               
                  echo "Successfully creating war file"

            }
            // post {
            //     success {
                   
            //         // Archive the .war file generated in the "target" directory
            //         archiveArtifacts artifacts: 'target/*.war'
            //          echo 'Archiving the Artifacts'
            //     }
            // }
        }
        stage ('Deploy to tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'tomcatcreds', path: '', url: 'http://13.51.108.55:9092/')], contextPath: 'helloworld', war: '**/*.war'
            }
        }
    }
}
