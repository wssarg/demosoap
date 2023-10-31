**SOAP Web Service + Spring Boot 3 (3.1.15) + JPA [JDK 17]**

1. Creamos el proyecto y agregamos las dependencias:
* Spring Boot DevTools
* Spring Web
* Spring Web Services
* Spring Data JPA
* H2 Database (puede variar)
* Lombok

2. Abrimos el proyecto en el IDE y:
   2.1. Creamos los paquetes: config, enpoint, repository, model, converter
   2.2. En resource, creamos la carpeta xsd
   2.3. En el application.properties:
   ```
   spring.datasource.url=jdbc:h2:mem:demosoap
   spring.datasource.driverClassName=org.h2.Driver
   spring.datasource.username=sa
   spring.datasource.password=password
   spring.jpa.database-platform=org.hibernate.dialect.H2Dialect
   ```

3. En el pom, agregamos:
* La dependencia wsdl4j
* El plugin de jaxb2-maven-plugin
  Ambos se encuentran en:
  https://github.com/wssarg/demosoap/blob/spring-boot-2/pom.xml

4. En resources, en xsd, creamos el archivo products.xsd
   https://github.com/wssarg/demosoap/blob/spring-boot-2/src/main/resources/xsd/products.xsd

5. Ejecutamos mvn compile para crear las clases del paquete gen.
   Nota 1: Si ya tienes una carpeta target, elimínala antes de ejecutar el comando.
   Nota 2: El paquete gen solo se creará en target, no en tu código, pero sí lo podrás usar.

6. En model, creamos la clase ProductModel
   https://github.com/wssarg/demosoap/blob/spring-boot-2/src/main/java/com/example/demosoap/model/ProductModel.java
   Nota: Las anotaciones deben ser importadas de javax

7. En converter, creamos la clase ProductConverter
   https://github.com/wssarg/demosoap/blob/spring-boot-2/src/main/java/com/example/demosoap/converter/ProductConverter.java

8. En config, crear la clase WebServiceConfig
   https://github.com/wssarg/demosoap/blob/spring-boot-2/src/main/java/com/example/demosoap/config/WebServiceConfig.java

9. En repository, crear la interfaz ProductRepository
   https://github.com/wssarg/demosoap/blob/spring-boot-2/src/main/java/com/example/demosoap/repository/ProductRepository.java

10. En endpoint, crear la clase ProductEndpoint
    https://github.com/wssarg/demosoap/blob/spring-boot-2/src/main/java/com/example/demosoap/endpoint/ProductEndpoint.java

11. En la raíz del proyecto, crear el archivo demosoap-soapui-project.xml
    https://github.com/wssarg/demosoap/blob/spring-boot-2/demosoap-soapui-project.xml

12. Iniciar la aplicación (mvn spring-boot:run)

13. Importamos demosoap-soapui-project.xml en SOAP-UI y probamos el proyecto.
