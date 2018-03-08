// start of pipeline
pipeline {
  // where pipeline job will run
  agent {
    label "master"
  }
  
  // start of stages : build, test, deploy ...
  stages {
    // start of stage : build
    stage('build') {
      // start of running steps inside one stage
      steps {
        // invoke command to build with maven
        bat 'mvn clean install'
      }
    }
    
        // start of deploy state
    stage('deploy') {
      // define step to run
      steps {
        //invoke command to stop tomcat service
        bat 'sc stop Tomcat9.0'
        //bat 'ping 127.0.0.1 -n 6'
        // copy war file from build target to webapp Tomcat folder
        bat 'xcopy /y C:\\Windows\\System32\\config\\systemprofile\\.jenkins\\workspace\\GOL_Pipeline\\gameoflife-web\\target\\gameoflife.war "C:\\Program Files\\Apache Software Foundation\\Tomcat 9.0\\webapps"'
        //invoke command to start tomcat service      
        bat 'sc start Tomcat9.0'
      }
    } 
  }
    
  } 
}

