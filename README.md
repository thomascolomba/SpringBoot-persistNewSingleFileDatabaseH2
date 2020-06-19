compile & execute :<br/>
mvn spring-boot:run<br/>
<br/>
compile into fat jar then execute :<br/>
mvn clean package<br/>
java -jar target/simpleSetupConnectionH2-0.0.1-SNAPSHOT.jar<br/>
<br/>

During the first execution, the console shows : <br/>
No Customer with lastname Bauer was found<br/>
The application will add one now<br/>
<br/>
During the second execution, the console shows : <br/>
No Customer with lastname Bauer was found<br/>
The application will add one now<br/>
<br/>
--AccessingDataJpaApplication.java<br/>
if(repository.findByLastName("Bauer").size() == 0) {<br/>
&nbsp;&nbsp;log.info("No Customer with lastname Bauer was found");<br/>
&nbsp;&nbsp;log.info("The application will add one now");<br/>
&nbsp;&nbsp;repository.save(new Customer("Jack", "Bauer"));<br/>
} else {<br/>
&nbsp;&nbsp;log.info("a Customer with lastname Bauer was found");<br/>
&nbsp;&nbsp;Customer customer = repository.findByLastName("Bauer").get(0);<br/>
&nbsp;&nbsp;log.info(customer.toString());<br/>
}<br/>
--application.properties<br/>
spring.datasource.url=jdbc:h2:~/test1;DB_CLOSE_ON_EXIT=FALSE<br/>
spring.jpa.hibernate.ddl-auto=create-drop<br/>
<br/>
This create a database named "test1.mv.db" in my user directory.<br/> 