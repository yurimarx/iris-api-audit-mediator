## iris-api-audit-mediator
This is a ObjectScript Application to audit API methods requests.
Can be developed with Docker and VSCode,
can be deployed as ZPM module.

## Installation for development

Clone/git pull the repo into any local directory e.g. like it is shown below (here I show all the examples related to this repository, but I assume you have your own derived from the template):

```
$ git clone git@github.com:yurimarx/iris-api-audit-mediator.git
```

Open the terminal in this directory and run:

```
$ docker-compose up -d --build
```

## Installation with ZPM

zpm:USER>install iris-api-audit-mediator

## How it Works

1. Clone the project 
```
$ git clone git@github.com:yurimarx/iris-api-audit-mediator.git
```

2. Build and up the project source code
```
$ docker-compose up -d --build
```

3. My project create the User Defined Audit Event on build into iris.script file, with the command: 
```
Do ##class(Security.Events).Create("RESTAPI","Request","RESTAPI","REST API Requests")
```
4. Go to Management Portal -> System Administration -> Security -> Auditing -> Configure User Events
5. See my event created, with: 
6. Set Event Source: RESTAPI 
7. Set Event Type: Request 
8. Set Event Name: RESTAPI
9. In this case is not necessary, but if you need create other audit events with other types and names, use the button Create New Event
10. Populate your Person app with data, call the endpoint http://localhost:52773/crud/persons/populate
11. Now, call http://localhost:52773/crud/persons/all, or any other endpoint
12. This request will be registered into Audit database
13. Now Go to Management Portal -> System Administration -> Security -> Auditing -> View Auditing Database
14. Looking for rows with Event Source RESTAPI and Event Type Request and click Detail to see audit record details.
15. Enjoy!


# Future features

1. Config custom audit messages

# Thanks to:

1. Robert Cemper: beta tester
2. Evgeny Shvarov: iris-rest-api-template was the base to this app