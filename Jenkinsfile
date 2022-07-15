node('built-in') 
{
    stage('ContinuousDownload')
    {
    git 'https://github.com/srinath111/mymaven.git'
    }
    stage('ContinuousBuilt')
    {
    sh 'mvn package'
    }
     stage('ContinuousDeployment')
    {
    deploy adapters: [tomcat9(credentialsId: '74cb3562-c5c2-4c17-8072-85fe27d7c86c', path: '', url: 'http://172.31.2.180:8080')], contextPath: 'testapp', war: '**/*.war'
    }
      stage('ContinuousTesting')
    {
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    
    sh 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline1/testing.jar'
    }
    stage('ContinuousDeliver')
    {
        input message: 'need approvals from DM', submitter: 'sri'
    deploy adapters: [tomcat9(credentialsId: 'a8446fea-4a9c-42b0-99cb-1cdc739ef10d', path: '', url: 'http://172.31.5.146:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
