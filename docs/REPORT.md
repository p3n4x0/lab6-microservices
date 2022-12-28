# REPORT

This document contains a brief of how the following activities have been accomplished:

- The two services `accounts (2222)` and `web` are running and registered (two terminals, logs screenshots).
- The service registration service has these two services registered (a third terminal, dashboard screenshots)
- A second `accounts` service instance is started and will use the port 4444. This second `accounts (4444)` is also
  registered (a fourth terminal, log screenshots).
- What happens when you kill the service `accounts (2222)` and do requests to `web`?  
  Can the web service provide information about the accounts again? Why?

## Steps
- First step is to run `registration` service.`./gradlew registration:bootRun`.
![Cap1.png](/docs/images/Cap1.png)

- Second step is to run `web` service.`./gradlew web:bootRun`.
![Cap2.png](/docs/images/Cap2.png)

- Third step is to run `accounts(2222)` service.`./gradlew accounts:bootRun`.
![Cap3.png](/docs/images/Cap3.png)

- Make sure all services have been launched correctly. To try it out we type localhost:1111 in 
the browser, where Eureka is allocated. And then, we can see both services (``accounts`` and ``web``) are allocated 
in Eureka(``registration``)
![Cap4.png](/docs/images/Cap4.png)

- Then we add a second accounts service instance, using the port 4444.
![Cap5.png](/docs/images/Cap5.png)

    Run it, then both ``accounts`` services will appear in Eureka
    ![Cap6.png](/docs/images/Cap6.png)


- Last step, kill ``accounts(2222)`` and then make request to web
![Cap7.png](/docs/images/Cap7.png)

Request didn't fail because web is not only looking for accounts(2222), it is looking for accounts service in general. 
Despite we had killed accounts(2222), accounts(4444) was still alived and ``web`` did the request to that microservice.
