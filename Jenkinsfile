pipeline {
      agent any
      stages {
            stage('Build Application') {
                  steps {
                        sh 'mvn clean package'
                  }
                  post {
                      success {
                          echo "Now archiving Artifacts..."
                          archiveArtifacts artifacts: '**/*.war'

                      }
                  }
            }
            stage('Deploy to staging') {
                build job: 'DeployApplicationStagingEnv'
            }
      }
}