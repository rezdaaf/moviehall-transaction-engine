# moviehall-transaction-engine

This project was made to complete assignment at the end of the training session for internship at tiket.com

Author: Rezda Abdullah Fachrezzi (Backend Engineer Intern)

## Description

This service holds data for User and Their Transaction. The data are stored in User and Reservation entity / table.

## Setup

What you need to have and set up before running this service

1. Java 11
2. MySQL
3. Your favorite IDE

Update below fields in the `application.properties`

```
spring.datasource.url=jdbc:mysql://<host>:<port>/<dbname> // change the <words> with your setting
spring.datasource.username= // your mysql username
spring.datasource.password= // your mysql password
```

Create tables using below queries to set up the database

User
```sql
CREATE TABLE `user` (
  `id` int NOT NULL AUTO_INCREMENT,
  `name` varchar(255) NOT NULL,
  PRIMARY KEY (`id`)
)
```

Reservation
```sql
CREATE TABLE `reservation` (
  `id` int NOT NULL AUTO_INCREMENT,
  `user_id` int NOT NULL,
  `hall_id` varchar(255) NOT NULL,
  `seat_id` varchar(255) NOT NULL,
  `active` tinyint NOT NULL,
  PRIMARY KEY (`id`)
)
```

## Run

You can run the service from the main application

## API

### `GET` /api/user
Find all users

#### Request Query
1. name `string` : to search all users containing the name

#### Response Example
```JSON
[
    {
        "id": 1,
        "name": "Bedul"
    }
]
```

### `GET` /api/user/{id}
Find user by id

#### Request Params
1. id `int` : user id

#### Response Example
```JSON
{
    "id": 1,
    "name": "Bedul"
}
```

### `POST` /api/user
Create new user

#### Request Body
1. name `string` : user name

#### Response Example
```JSON
{
    "id": 1,
    "name": "Bedul"
}
```

### `PUT` /api/user/{id}
Update user by id

#### Request Params
1. id `int` : user id

#### Request Body
1. name `string` : user name

#### Response Example
```JSON
{
    "id": 1,
    "name": "Bedul"
}
```

### `DELETE` /api/user/{id}
Delete user by id

#### Request Params
1. id `int` : user id

#### Response Example
```JSON
```

### `GET` /api/reservation
Find all reservation

#### Request Query
1. userId `int` : to search all reservation with associated user id

#### Response Example
```JSON
[
    {
        "id": 1,
        "userId": 1,
        "seatId": "fdsfsfd43",
        "hallId": "fdsfs5435",
        "name": "Bedul",
        "active": true,
    }
]
```

### `GET` /api/reservation/active
Find all active reservation

#### Request Query
1. userId `int` : to search all reservation with associated user id

#### Response Example
```JSON
[
    {
        "id": 1,
        "userId": 1,
        "seatId": "fdsfsfd43",
        "hallId": "fdsfs5435",
        "name": "Bedul",
        "active": true,
    }
]
```

### `GET` /api/reservation/{id}
Find reservation by id

#### Request Params
1. id `int` : reservation id

#### Response Example
```JSON
{
    "id": 1,
    "userId": 1,
    "seatId": "fdsfsfd43",
    "hallId": "fdsfs5435",
    "name": "Bedul",
    "active": true,
}
```

### `POST` /api/reservation
Create reservation

#### Request Body
1. id `int` : user id who make a reservation
2. row `int` : seat row
3. number `int` : seat number
4. hallId `string` : desired movie hall id

#### Response Example
```JSON
{
    "id": 1,
    "userId": 1,
    "seatId": "fdsfsfd43",
    "hallId": "fdsfs5435",
    "name": "Bedul",
    "active": true,
}
```
