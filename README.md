# configclientcheck
Repository related to config client code in spring boot

Below are the steps to create a Sprint cloud config client project
1. Create a Spring boot project
2. In build.gradle add 'org.springframework.cloud:spring-cloud-starter-config' dependency
3. If you are creating project from scratch and adding the above dependency using Spring Initializer then below thing will come automatically but if you already created project and want to add dependency separately then you need to add below thing also in you build.gradle file:
   1. ext {
      set('springCloudVersion', "2023.0.4")
      }
   2. dependencyManagement {
      imports {
      mavenBom "org.springframework.cloud:spring-cloud-dependencies:${springCloudVersion}"
      }
      }
4. In application.properties file add 'spring.config.import' key and provide cloud config server url and before server url add 'optional:configserver:' (Example -> spring.config.import=optional:configserver:http://localhost:8888)
5. If you want to add some file in config which is specific to only your project then in Config repo create those file with your application/project name and yml in the end, like for this project I created a file configclientcheck.yml
6. To achieve step 5, in this project/application(configclientcheck) we need to add 'spring.application.name' in our application.properties file.


Reference URL : https://www.youtube.com/watch?v=E2HkL766VHs




How to Use Dynamic refresh (Refresh of config values):
1. In Spring client project add 'org.springframework.boot:spring-boot-starter-actuator' dependency
2. In application.properties file add this (management.endpoints.web.exposure.include=*) property
3. If above value you are adding in properties file then don't add * inside double quote but if you are adding in yml file then add * inside double quote
4. In all classes where you are using @Value annotation on all those classes add @RefreshScope annotation

For Refresh : https://www.youtube.com/watch?v=yNnLICy2zk4


Best Practice of Spring cloud config: https://www.youtube.com/watch?v=AiGCx0raQfs



