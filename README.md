# Questions
1. What does operator do? how can he insert measurements? -> refers to API
2. What are variants in use case? adding network, gateways or sensors are different variants?
3. Do we need to add requirements for the sensors? like battery's life etc...


# Requirements Document - GeoControl

Date:

Version: V1 - description of Geocontrol as described in the swagger

| Version number | Change |
| :------------: | :----: |
|  |        |

# Contents

- [Requirements Document - GeoControl](#requirements-document---geocontrol)
- [Contents](#contents)
- [Informal description](#informal-description)
- [Business model](#business-model)
- [Stakeholders](#stakeholders)
- [Context Diagram and interfaces](#context-diagram-and-interfaces)
  - [Context Diagram](#context-diagram)
  - [Interfaces](#interfaces)
- [Stories and personas](#stories-and-personas)
- [Functional and non functional requirements](#functional-and-non-functional-requirements)
  - [Functional Requirements](#functional-requirements)
  - [Non Functional Requirements](#non-functional-requirements)
- [Use case diagram and use cases](#use-case-diagram-and-use-cases)
  - [Use case diagram](#use-case-diagram)
    - [Use case 1, UC1](#use-case-1-uc1)
      - [Scenario 1.1](#scenario-11)
      - [Scenario 1.2](#scenario-12)
      - [Scenario 1.x](#scenario-1x)
    - [Use case 2, UC2](#use-case-2-uc2)
    - [Use case x, UCx](#use-case-x-ucx)
- [Glossary](#glossary)
- [System Design](#system-design)
- [Deployment Diagram](#deployment-diagram)

# Informal description

GeoControl is a software system designed for monitoring physical and environmental variables in various contexts: from hydrogeological analyses of mountain areas to the surveillance of historical buildings, and even the control of internal parameters (such as temperature or lighting) in residential or working environments. 

//TO DO: finish the description

# Business Model
Who?
Public and private companies requiring continuous monitoring of physical parameters.

Why?
Provide monitoring of physical parameters in order to automatize process.

Money flow?
Commissioned by Union of mountain communities, and commercialized to private enrtities


# Stakeholders

| Stakeholder name | Description |
| :--------------: | :---------: |
| Commissioner  |             |
| Private companies  |             |
| Developer team  |             |
| Administation  |             |
| User  |             |
| Sensors providers  |             |
| Cloud service provider  |             |
| Maintainance staff |             |

# Context Diagram and interfaces

## Context Diagram

\<Define here Context diagram using UML use case diagram>

\<actors are a subset of stakeholders>

## Interfaces

\<describe here each interface in the context diagram>


|   Actor   | Logical Interface | Physical Interface |
| :-------: | :---------------: | :----------------: |
| gateway | API, serial connection | Internet connection for api and electrical informations through cables to sensors |
| sensors | serial connection | electrical informations through cables to sensors to gateway |
| users | Website | screen and keyboard |
| administator | Website | screen and keyboard |
| Cloud service provider | API | internet connection |
| maintainance staff | diagnostic, firmare upgrade | sensors'port |


# Stories and personas

\<A Persona is a realistic impersonation of an actor. Define here a few personas and describe in plain text how a persona interacts with the system>

\<Persona is-an-instance-of actor>

\<stories will be formalized later as scenarios in use cases>

# Functional and non functional requirements

## Functional Requirements

\<In the form DO SOMETHING, or VERB NOUN, describe high level capabilities of the system>

\<they match to high level use cases>

|  ID   | Description |
| :---: | :---------: |
|  FR1  | Authentication and User Management |
|  FR1.1 | Login by user and password|
|  FR1.1.1 | generate Access token |
|  FR1.2 | Logout |
|  FR1.3 | Admin creates a new user |
| FR1.4| Change user's role |
| FR1.5| Change password |
|  FR2 | Topology Management and Synchronization |
| FR 2.1 | CRUD networks(identified by IP address) |
| FR 2.2 | CRUD gateways(identified by MAC address) |
| FR 2.3 | CRUD sensors(idientified by MAC address of associated gateway) |
|  FR 3 | Measurement Collection and Storage |
| FR 3.1 | Retrieve data from sensors |
| FR 3.1.1 | Filer on sensor id |
| FR 3.1.2 | Filer on date range |
| FR 3.1.3 | retrieve only outliers |
| FR 3.4 | retireve statistics |
| FR 3.4 | retireve measurements |
| FR 3.2| convert to ISO8601 |
| FR 3.3 | Store data into DBs|
| FR4 | Calculations and Statistical Analysis |
| FR4.1 | Compute mean |
| FR4.2 | Compute variance |
| FR4.3 | identify potential anomalous values |
| FR4.4 | identify outliers |
| FR 5 | Display data |

## Non Functional Requirements

\<Describe constraints on functional requirements>

|   ID    | Type (efficiency, reliability, ..) | Description | Refers to |
| :-----: | :--------------------------------: | :---------: | :-------: |
|  NFR1   | Reliability |  no more than six measurements per year, per sensor, are lost | F3.1 |
|  NFR2   | Reliability | data should have a Back-up | FR1, FR2, FR3 |
|  NFR3   | Security | Api communications should use HTTPS | FR1, FR2, FR3 |
|  NFR4   | Efficiency | time require to login is less than 1min | FR1.1 |
|  NFR5   | Usability | Time required for create a new user is less than 5min for someone who's a computer user since 1 year| FR 1.3|
|  NFR6   | Usability | Time required for learn how to use the program for view data 10 minutes  | FR 5 |
|  NFR7   | Portability | Website should be viewed from browser on smartphone | FR1, FR5 |

# Use case diagram and use cases

## Use case diagram

\<define here UML Use case diagram UCD summarizing all use cases, and their relationships>

\<next describe here each use case in the UCD>

### Use case 1: Login

| Actors Involved  |                                                                      |
| :--------------: | :------------------------------------------------------------------: |
|   Precondition   | User already has an account |
|  Post condition  | user is autheticated |
| Nominal Scenario | User insert username and password and receives access token |
|     Variants     | No variants |
|    Exceptions    | User insert wrong password, user doesn't have an account, recover password |

##### Scenario 1.1

\<describe here scenarios instances of UC1>

\<a scenario is a sequence of steps that corresponds to a particular execution of one use case>

\<a scenario is a more formal description of a story>

\<only relevant scenarios should be described>

|  Scenario 1.1  |                                                                            |
| :------------: | :------------------------------------------------------------------------: |
|   Precondition   | User already has an account |
|  Post condition  | user is autheticated |

|     Step#      | Actor | Description |
| :-----: | :--------------------------------: | :---------:|
|     Step#      | Actor | Description |
|       1        | user | User insert username |
|       2        | user | User insert password |
|       3        | server | check username passoword corrispondence |
|       4        | server | sends access token |

### Use case 2, Admin creates a new user

| Actors Involved  |                                                                      |
| :--------------: | :------------------------------------------------------------------: |
|   Precondition   | Admin is authenticated |
|  Post condition  | new user is created |
| Nominal Scenario | Admin choose username and password, that are validated, and a new user is added to db |
|     Variants     | No variants |
|    Exceptions    | Username already exists, password is not valid |

##### Scenario 2.1

|  Scenario 1.1  |                                                                            |
| :------------: | :------------------------------------------------------------------------: |
|   Precondition   | Admin is authenticated |
|  Post condition  | new user is created |

|     Step#      | Actor | Description |
| :-----: | :--------------------------------: | :---------:|
|       1        | admin | admin insert username |
|       2        | sever | server check username is unique |
|       3        | admin | Admin insert password |
|       4        | server | check passoword is valid |
|       5        | server | create new entry in the database |
|       6        | server | sends successful message |

### Use case 3, view statistics 

| Actors Involved  |                                                                      |
| :--------------: | :------------------------------------------------------------------: |
|   Precondition   | User is authenticated |
|  Post condition  | User can view the data |
| Nominal Scenario | User select some filter and data are displayed |
|     Variants     | show measurements, stats or outliers for all sensors, or for a specific one |
|    Exceptions    | Network, gateway or sensors id are not valid |

##### Scenario 3 

|  Scenario 3  |                                                                            |
| :------------: | :------------------------------------------------------------------------: |
|   Precondition   | User is authenticated |
|  Post condition  | User can view the data |

|     Step#      | Actor | Description |
| :-----: | :--------------------------------: | :---------:|
|       1        | user | User selects sensors, gateway or nerwork id |
|       2        | system | checks user validity |
|       3        | system | compute statistics  |
|       4        | system | compute thresholds |
|       5        | system | detects outliers |
|       6        | system | sends data |


### Use case 4, Topology management

| Actors Involved  |                                                                      |
| :--------------: | :------------------------------------------------------------------: |
|   Precondition   | Operator is authenticated |
|  Post condition  | New topology element is added |
| Nominal Scenario | Operator add network's data |
|     Variants     |  |
|    Exceptions    | Username already exists, password is not valid |

##### Scenario 4 Topology management

|  Scenario 3  |                                                                            |
| :------------: | :------------------------------------------------------------------------: |
|   Precondition   | User already has an account |
|  Post condition  | user is autheticated |

|     Step#      | Actor | Description |
| :-----: | :--------------------------------: | :---------:|
|       1        | user | User insert username |

//To do

# Glossary

\<use UML class diagram to define important terms, or concepts in the domain of the application, and their relationships>

\<concepts must be used consistently all over the document, ex in use cases, requirements etc>

# System Design

\<describe here system design>

\<must be consistent with Context diagram>

# Deployment Diagram

\<describe here deployment diagram >

