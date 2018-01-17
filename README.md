# RESTful API w/Spring Boot, Maven & MongoDB
###### git clone ➡ install & launch MongoDB ➡ run the application w/Maven

instructions for installing & launching MongoDB:
* brew install:
```
$ brew install mongodb
```
* launch the mongo daemon
```
$ mongod
```
* open another terminal window and launch the MongoDB client
```
$ mongo
```

run the application w/Maven
 ```
$ ./mvnw spring-boot:run 
```

For CRUD functionality refer to the below commands once the application is running

hit localhost:8080
```
$ curl http://localhost:8080
```
![localhost:8080](./screenshots/localhost-8080.png)

hit localhost:8080/people
```
$ curl http://localhost:8080/people
```
![localhost:8080/people](./screenshots/localhost-8080-people.png)

POST new name to MongoDB
```
$ curl -i -X POST -H "Content-Type:application/json" -d "{ \"firstName\": \"Michael\", \"lastName"\: \"Jordan\" }" 
http://localhost:8080/people
```
![POST - localhost:8080/people](./screenshots/POST.png)

query all people to check that the POST worked
```
$ curl http://localhost:8080/people
```
![POST - localhost:8080/people](./screenshots/POST.png)

OR hit the new MJ end-point to check that the POST worked
```
$ curl http://localhost:8080/people/5a5ec01d945d8c3cefcf35ed
```
![localhost:8080/people/5a5ec01d945d8c3cefcf35ed](./screenshots/localhost-8080-people-check-direct.png)

find all custom queries
```
$ curl http://localhost:8080/people/search
```
![localhost:8080/people/search](./screenshots/custom-queries.png)

to use findByLastName
```
$ curl http://localhost:8080/people/search/findByLastName?name=Jordan
```
![localhost:8080/people/search/findByLastName?name=Jordan](./screenshots/findByLastName.png)

PUT to change Michael Jordan entry to Ash Ketchum
```
$ curl -X PUT -H "Content-Type:application/json" -d "{ \"firstName\": \"Ash\", \"lastName\": \"Ketchum\" }"
```
![PUT](./screenshots/PUT.png)

PATCH to change Ash to Trainer
```
$ curl -X PATCH -H "Content-Type:application/json" -d "{ \"firstName\": \"Trainer\" }" http://localhost:8080/people/5a5ec01d945d8c3cefcf35ed
```
![PATCH](./screenshots/PATCH.png)

DELETE to change Ash to Trainer
```
$ curl -X DELETE http://localhost:8080/people/5a5ec01d945d8c3cefcf35ed
```
![DELETE](./screenshots/DELETE.png)

curl http://localhost:8080/people/5a5ec01d945d8c3cefcf35ed one more time to confirm the DELETE