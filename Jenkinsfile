pipeline
{
    agent any
    tools 
    {
        maven 'M2_HOME'
    }
    stages
    {
        stage('CheckOut')
        {
            steps
            {
             checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sri576/webpages.git']]])   
            }
        }
        stage('Build')
        {
            steps
            {
                sh 'mvn clean install -f MyWebApp/pom.xml'
            }
        }
        stage('QualityCheck')
        {
            steps
            {
                echo 'code checking sucessfully'
            }
        }
        stage('Deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'deploy', path: '', url: 'http://13.234.76.49:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
