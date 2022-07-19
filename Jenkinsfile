if (currentBuild.getBuildCauses().toString().contains('BranchIndexingCause')) {
  print "INFO: Build skipped due to trigger being Branch Indexing"
  currentBuild.result = 'ABORTED' // optional, gives a better hint to the user that it's been skipped, rather than the default which shows it's successful
  return
}
pipeline {
    agent any

    stages {
        stage('dev') {
            when {
                branch 'feature'
            }
            steps {
                echo 'from feature branch..'
            }
        }
        stage('QA') {
            when {
                branch 'develop'
            }
            steps {
                echo 'from develop branch'
            }
        }
        stage('prod') {
            when {
                branch 'master'
            }
            steps {
                echo 'from master branch'
            }
        }
    }
}
