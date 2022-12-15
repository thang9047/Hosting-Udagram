# Udagram

- [Udagram](#udagram)
  - [Description](#description)
    - [Dependencies](#dependencies)
    - [AWS Cloud Setup](#aws-cloud-setup)
  - [Environment Variables](#environment-variables)
  - [Pipeline](#pipeline)
  - [CircleCi](#circleci)
  - [Testing](#testing)
    - [Unit Tests:](#unit-tests)
    - [End to End Tests:](#end-to-end-tests)
  - [Built With](#built-with)

---

## Description
A more in depth documentation into the application.

### Dependencies

```
- Node v14.15.1 (LTS) or more recent

- npm 6.14.8 (LTS) or more recent

- AWS CLI v2

- AWS EB CLI

- AWS RDS database running Postgres.

- AWS S3 bucket for Frontend.

- AWS Elastic Beanstalk for Backend.

```

### AWS Cloud Setup

- RDS - Database Host: database-3.cjyqjeiynmkt.us-east-1.rds.amazonaws.com
- RDS - Database Port: 5432
- RDS - Database Name: postgres

- S3 Endpoint - Frontend: http://thangdd12-udagram.s3-website-us-east-1.amazonaws.com/home

- Elastic Beanstalk URL - Backend: http://udagram-api-dev.eba-itq5cieq.us-east-1.elasticbeanstalk.com/

## Environment Variables

Setup the following variables in the .env file or in the cloud environments:
```
- PORT                = 8080
- POSTGRES_HOST       = database-3.cjyqjeiynmkt.us-east-1.rds.amazonaws.com
- POSTGRES_PORT       = 5432
- POSTGRES_DB         = postgres
- POSTGRES_USERNAME   = postgres
- POSTGRES_PASSWORD   = mypassword
- URL                 = http://thangdd12-udagram.s3-website-us-east-1.amazonaws.com/home
- JWT_SECRET          = 5ae8adc9731627905ebf0905dbe4a114ba7d8354ae1796772dfa523a2142761b78d48cbfcd98000bb94fbdbd8147f30de6b3484c3a060d389068204df6a50630
- AWS_REGION          = us-east-1
- AWS_PROFILE         = default
- AWS_BUCKET          = thangdd12-udagram

AWS_ACCESS_KEY_ID = "AKIA2UX5GF4YT2XD6FFX"
AWS_SECRET_ACCESS_KEY = "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"
```

## Pipeline

From the root of the project:
- `npm run frontend:install`    - To install frontend dependencies.
- `npm run frontend:build`      - To build the Angular/Frontend.
- `npm run frontend:deploy`     - To deploy the project to S3 using `./udagram-frontend/bin/deploy.sh` deploy script.
- `npm run api:install`     - To install backend dependencies.
- `npm run api:build`       - To transpile the Typescript/Backend.
- `npm run api:deploy`      - To deploy the project to EB using `./udagram-api/bin/deploy.sh` deploy script.
## CircleCi

The order of the run jobs:
- Setting Env Variables.
- Install NodeJS.
- Checkout Code & Cloning the Repo.
- Install AWS CLI v2.
- Check & Disable AWS pager.
- Configure AWS AccessKeyID.
- Configure AWS Region.
- Frontend:
  - Install dependencies.
  - Build the angular.
  - Deploy the site to AWS S3.
- Backend:
  - Install dependencies.
  - Transpile the typescript/ build the app.
  - Install AWS Elastic Beanstalk CLI.
  - Deploy the app to AWS Elastic Beanstalk.

## Testing

This project contains two different test suite: unit tests and End-To-End tests(e2e). Follow these steps to run the tests.

1. `cd udagram/udagram-frontend`
2. `npm run test`
3. `npm run e2e`

There are no Unit test on the back-end

### Unit Tests:

Unit tests are using the Jasmine Framework.

### End to End Tests:

The e2e tests are using Protractor and Jasmine.

## Built With

- [Angular](https://angular.io/) - Single Page Application Framework
- [Node](https://nodejs.org) - Javascript Runtime
- [Express](https://expressjs.com/) - Javascript API Framework
