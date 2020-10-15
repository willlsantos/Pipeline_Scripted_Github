pipeline {
    agent any
    stages {
        stage('Git-Checkout') {
            steps {
                    echo "Checking out from Git Repo";
                    git credentialsId: '3bf5ed2c-c4bb-406b-83c7-a4c3bce88e18', url: 'https://github.com/willlsantos/Pipeline_Scripted_Github.git'
                    /* Put in the actual Code for checking out code from your Git Repo here */
            }
        }
        
        stage('Build') {
            steps {
                    echo "Building the checked-out project!";
                    sh "chmod +x -R ${env.WORKSPACE}"
                    sh './build.sh'
                     /* Put in the actual Code for Executing Build.bat file from your Git Repo here */
            }
        }
        
        stage('Unit-Test') {
            steps {
                    echo "Running JUnit Tests"; 
                    sh "chmod +x -R ${env.WORKSPACE}"
                    sh './unit.sh'
                    /* Put in the actual Code for Executing Unit.bat file from your Git Repo here */
             }
        }
        
        stage('Quality-Gate') {
            steps {
                  echo "Verifying Quality Gates";
                  sh "chmod +x -R ${env.WORKSPACE}"
                  sh './quality.sh'
                  /* Put in the actual Code for Executing Quality.bat file from your Git Repo here */

            }
        }
        
        stage('Deploy') {
            steps {
                  echo "Deploying to Stage Environment for more tests!";
                  sh "chmod +x -R ${env.WORKSPACE}"
                  sh './deploy.sh'
                  /* Put in the actual Code for Executing Deploy.bat file from your Git Repo here */
            }
        }
    }
    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}