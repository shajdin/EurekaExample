# EurekaExample


Eureka example application. 

##To run locally set "dev" profile, and run projects. 

##To run on Pivotal Web Services (PWS):
  1) run maven clean package

  2) install Cloud Foundry CLI (OSX with homebrew: brew install cf-cli), and create PWS account

  3) in command line run: "cf login -a https://api.run.pivotal.io"

  4) for each project position yourself in project folder and run "cf push"
  
  5) for User and Web projects go to their page on PWS, tab "Env Variables" and add enviroment variable: name="eureka.instance.hostname"(without quotes), and set value to application_uri provided by PWS below. For example in my app it looks like this 
  "application_uris": [
        "sh44794-bzvz-app-unpouched-uncordiality.cfapps.io"
  ].
  So (name, value) pair should be (eureka.instance.hostname, sh44794-bzvz-app-unpouched-uncordiality.cfapps.io).
  
  6) If no database service is bind to app User project will create embedded database. Optionally you can go to User project, Service tab and bind for example MySql database. Connect to that database and create User table: 
CREATE TABLE t_user(
id int NOT NULL AUTO_INCREMENT,
first_name varchar(255),
last_name varchar(255),
username varchar(255),
PRIMARY KEY (id)).
PWS autoconfigures dataSource.
  
