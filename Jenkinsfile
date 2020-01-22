pipeline {

agent any

stages
{

stage('cloning code')

{

steps

{git branch: 'mynewwbranch', url: 'https://github.com/santosh13194/maven-project.git'
}
}

stage('compile my project')
{
steps
{
withMaven(jdk: 'Java', maven: 'Maven') {
    sh 'mvn compile'
}}}
    
stage('test my project')
{
steps
{
withMaven(jdk: 'Java', maven: 'Maven') {
    sh 'mvn test'
}}}
    
stage('package my project')
{
steps
{
withMaven(jdk: 'Java', maven: 'Maven') {
    sh 'mvn package'
}}}
    

    
        
stage('package my install')
{
steps
{
withMaven(jdk: 'Java', maven: 'Maven') {
    sh 'mvn install'
}}}
	
   
	
	
stage('deploy to  tomcat')
{
steps
{
    sshagent(['tomcat']) {
	 sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.39.255:/var/lib/tomcat/webapps'
						}
}
}
    
	
     
    

}
}
