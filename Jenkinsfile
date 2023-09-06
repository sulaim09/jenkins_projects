pipeline{
    agent any 
    tools {
        maven 'Maven' 
    }
    stages{
        stage("Test"){
            steps{
                // mvn test
                sh "mvn test"
                echo "Execution..."       
            }
        }
        stage("Build"){
            steps{
              // mvn package  
              sh "mvn package"
               echo "========Execution-===========..." 
            }
        }
        stage("Deploy on Test"){
            steps{
                // deploy on conatiner ---> pulgin
                sh '''deploy adapters: [tomcat9(path: '', url: 'http://54.80.60.47:8080//')], contextPath: 'app', war: '**/*.war''''
                echo "========Execution-===========..."
               
            }
        }
        stage("Deploy on Prod"){
            steps{
                 // deplo on prod
                echo "Deploying the project..."
               
            }
        }    
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
            
        }
        failure{
            echo "========pipeline execution failed========"
            
        }
    }
}
