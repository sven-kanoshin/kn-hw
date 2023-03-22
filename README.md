# K+N Homework Docker Compose APP
K+N Homework Consolidated Project

### Get Code

Recursive clone

`git clone --recurse-submodules -j8 https://github.com/sven-kanoshin/kn-hw.git`

### Build and Run

`docker compose up -d`

This will build the Docker images of the submodules and run the system as well.
In the end, the app will be accessible at `http://localhost:8080`

### Stop 

`docker compose down`

Will stop the whole app

# K+N Homework Frontend: Some notes about this cities-list app by the developer

## users

admin/admin - will be able to edit the name and image of the cities
user/password - will only be able to browse/search the list (but not edit)

## other notes

The session lasts for 60 minutes (as configured in the BE) so if some browsing/searching/editing is tried after that the user will be "logged out" in FE as well and directed to login page

Search bar works so that a new request is not done before 1 second has passed since the last keystroke (to avoid a lot of unnecessary requests)

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

# K+N Homework Backend

RESTful backend.

## Building

### Requirements
JDK17

### Build command

`gradlew clean build`

### Run as deploy pack
`java -jar kn-homework.jar`

### Dockerization
## Build
`docker build -t kn-hw-be .`

## Run
`docker run -d --name=kn-hw-be -p9090:8666 kn-hw-be:latest`

With the given configuration, the Swagger will be located at `http://localhost:9090/kn/swagger-ui.html`

## Using

### Frontend
**Note:** The matching Frontend project is at `https://github.com/raulmetsva/city-list`

### Accessing the Backend

After running the application (with the default configuration) it will repond on: `http://localhost:8666/kn/api/{endpoint}`

The documentation is provided via Swagger and can be accessed at: `http://localhost:8666/kn/swagger-ui.html`

### Using the Backend

First step is to login. Post a JSON (`Content-Type: application/json`) body containing the username and credentials (`{"username":"{username}", "credentials":"{password}"}`) against the login endpoint (`http://localhost:8666/kn/api/login`).
 
**Note:** Currently only JSON body login is supported. Can be extended with "form-data" if required

The response will contain a "token" attribute. For subsequent request use the token as Bearer token: `Authorization: Bearer {token}`. 

With the bearer token set, the cities endpoints are now accessible: `GET http://localhost:8666/kn/api/cities`. More info in Swagger documentation

### Users and permissions
For the demo, the users are included in the application

 - "anon:" (empty password) - "ANON" role -  No permissions
 - "user:password" - "USER" role - 'View' permissions
 - "admin:admin" - "ADMIN" role - 'View' and 'Edit' permissions
 
# Team Way-of-Work
## Team Setup
One Frontend person, one Backend person. Working in a "remote work" configuration, ie team was separated but had in person status and discussion meetings. From implementation side, Backend was the front-runner: implementing features and offering them to Frontend when the features were ready. In essence, Backend defined the architecture and application communication design, while Frontend implemented the integration by API spec.
## Timeframe 
Backend - ~30h
Frontend - ~22h 
## Benefits of working with team vs solo
Specialization and dicussions. 
Specialization means, the team member can dig deep into a specific topic without the whole project stalling. Other members can keep developing at the same time. Discussions and different ideas are always welcome, but become imperative when being stuck in a situation. Digging yourself out of a hole is much easier, when there is another person who is helping you.
 