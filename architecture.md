# National Sandwich Shop Online Ordering System
This document describes architecture design for National Sandwich Shop Online Ordering System

Author: Jakub Sowiński

Status: In progress

Last updated: 30-05-2022


## Context
A national sandwich shop wants to enable 'fax in your order' but over the Internet instead (in addition to their current fax-in service)

- Users: thousands, perhaps one day millions
- Requirements:
    - users will place their order, then be given a time to pick up their sandwich and directions to the shop (which must integrate with several external mapping services that include traffic information)
    - if the shop offers a delivery service, dispatch the driver with the sandwich to the user
    - mobile-device accessibility
    - offer national daily promotionals/specials
    - offer local daily promotionals/specials
    - accept payment online or in person/on delivery
- Additional Context:
    - Sandwich shops are franchised, each with a different owner.
    - Parent company has near-future plans to expand overseas.
    - Corporate goal is to hire inexpensive labor to maximize profit.


## Architectural drivers

### High-level functional requirements

#### Actors
Actors described below will be further referred to as (A1), (A2), (A3), etc.

| Name | Code | Description |
| --- | --- | --- |
| Customer | A1 | Sandwich shop customer, who can browse restaurants and order a sandwich from selected restaurant. |
| Franchise worker | A2 | Restaurant worker, who can offer local daily promotions/specials, and accept or decline (A1) orders. |
| Franchise owner | A3 | Restaurant owner, who can manage restaurant information in the system, and perform other tasks of (A2). |
| System admin | A4 | System administrator, who can offer national daily promotions/specials. |


#### Requirements
Requirements described below will be further referred to as (R1.1), (R1.3.2), (R2.1), etc.

1. As a Customer (A1), I want to be able to:
    1. Browse existing restaurants.
    2. Order from selected restaurant.
    3. Pay for my order online.
    4. Receive my order:
        1. Personally, in restaurant.
        2. Delivered to my location, if restaurant offers delivery service.
2. As a Franchise worker (A2), I want to be able to:
    1. Authenticate with the system.
    2. Receive Customer's (A1) order, if it was placed in my restaurant.
    3. Accept or decline Customer's (A1) order.
    4. Offer local daily promotions/specials.
3. As a Franchise owner (A3), I want to be able to:
    1. Perform the same tasks Franchise worker (A2) can.
    2. Manage information related to my restaurant in the system.
4. As a System admin (A4), I want to be able to:
    1. Perform the same tasks Franchise owner (A3) can for all the restaurants in the system.
    2. Offer national daily promotions/specials.


### Business limitations
Business limitations described below will be further referred to as (BL1), (BL2), (BL3), etc.

### Technical limitations
Technical limitations described below will be further referred to as (TL1), (TL2), (TL3), etc.

### Characteristics
Characteristics described below will be further referred to as (C1), (C2), (C3), etc.

## System (C1)

### System diagram
Systems included In this diagram will be further referred to as (S1), (S2), (S3), etc.

![System diagram](system-diagram-1.png)

### Use cases
Use cases included In this diagram will be further referred to as (UC1), (UC2), (UC3), etc.

![Use case diagram](use-case-diagram-0.png")

### Conceptual data model
![Conceptual data model diagram](conceptual-data-model-diagram-1.png)


## Containers (C2)

### Container diagram
Modules included in this diagram will be further referred to as (M1.1), (M1.2), (M1.3), etc.

Data stores included in this diagram will be further referred to as (DS1), (DS2), (DS3), etc.

![Container diagram](container-diagram-1.png)

### Use cases

#### (UC1) Customer browses restaurants

##### Use case diagram
![Use case diagram for UC1](use-case-diagram-1.png)

##### (UC1.1) Customer searches for restaurant

###### Sequence diagram
![Sequence diagram for UC1.1](sequence-diagram-1-1.png)

#### (UC2) Customer orders
![Use case diagram for UC2](use-case-diagram-2.png)

##### (UC2.2) Customer places order

###### Sequence diagram
![Sequence diagram for UC2.2](sequence-diagram-2-2.png)

## Decisions

### (ADR1) Decision to treat "specials" as menu items of different type

### (ADR2) Decision to separate Restaurants API from Orders API and Restaurants DS from Orders DS