pipeline {
   agent any
        stages {
            stage ('One') {
                 steps {
                      echo "Hi, I am Rajan Here"
                 }
            }        
             stage ('Two') {
                  steps {
                       input('Do you want to proceed?')
                  }
             } 
            stage ('Three') {
              when {
                 not {
                   branch "Master"
                 }
              }
              steps { echo "Hello" }
            }
            
            stage ('Four') {
                 parallel {
                     stage ('Unit test') {
                       steps { echo "Running the unit test" }
                     }
                     stage ('Pull docker image') {
                     agent {
                        docker {
                          reuseNode false
                          image 'ubuntu'
                        }
                     }
                     steps { echo "Running another test" }
                     }
                 }
            }
        }

}
