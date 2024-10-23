# Technologies used

- **`Next.js`** for server side rendering and building frontend
- **`Express.js`** is used for building backend
- **`Mongodb`** as database
- **`Mongoose`** as an ORM
- **`Typescript`** , backend is written entirely in typescript to prevent headaches you get when infinte number of events are flowing around with no hints
- **`Stripe`** for handling payments
- **`Jest and Supertest`** for testing 
- **`Docker`** for containerization
- **`Kubernetes`** for conatiner orchestration
- **`Skaffold`** command line tool that facilitates continuous development for Kubernetes-native applications. Makes working with and managing kubernetes 
                  and different kubernetes services and deploymets a lot easier.
- **`NATS Streaming`** is used as an event bus or message queue for publisihing and handling the events emitted by different services.
- **`Bull.js`** is a fast and robust queue system. It is used to implement the payment expiration timer.


# App Architecture

The app is divided into 7 services that handle and implement a specific feature and functionality of the app:

- `auth` handles the entire app authentication and authorization. JWT and cookie based authentication is used.
- `expiration` handles the payment expiration timer to make sure user pays within a specified time frame. 
- `orders` for handling user orders
- `payments` for handling stripe payments
- `tickets` for handling tickets(creating, updating, fetching). Instead of selling products, this e-commerce app sells tickets of different live events happening                    around the city.
- `common` all the common functionality like requireAuth, error handling, and other middlewares and functions shared by different services are grouped together. 
            This service is published as an npm package and installed in other services to be used. 
- `client` handles and implements the frontend of the app.
- `infra`  manages all the kubernetes deployment and service (.yaml) files that run run the app

#  Installation 

Getting this project up and running on your local machine is a notoriously dfficult task. It requires some knowlege of docker and kubernetes ecosystem. If you 
are still up for the challenge, or if you don't have a life, try getting it work. Make sure you have docker, kubernetes and skaffold installed. Set the required envirenmental variables and run the following command:

```
skaffold dev
```

And boom app will be up and running, no extra setup and dependencies required.

To delete any resources deployed by Skaffold and stop all the deployments, services and containers run 

```
skaffold delete
```

