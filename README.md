# Database
### User Stories:
* As a user I would like to have a list of Heros.
* As a user I would like to have a list of Villains.
* As a user I would like to see what abilities the heroes and villains have.
* As a user I would like to see what damage the Heroes have.
* As a user I would like to see what damage the Villains have.
* As a user I would like to see what combined damage the enemies and heroes have with their abilities.

### ERD Design:
![erd design](https://user-images.githubusercontent.com/31927590/38927921-296ad312-42ff-11e8-808d-7d657d531e26.jpg)
### Data Dictionary
Below is a screenshot of my data dictionary. My data dictionary has been created to help people understand the data base with all of the information in front of them instead of seeing it in the actual database itself. The data dictionary will show the types of inputs that will go with each field. Data dictionaries are important as they can keep the database consistent from the start by giving it a set point. This allows viewers to look onto a clear view of what the database is going to be like and can always be referred to when putting the database together.
This data dictionary shows how my database will be designed and what the type of each field is. I will be able to use this dictionary as a fixed layout of the database when creating the final piece. I know what I must add, and I know it’s everything I need.

![data dictionary](https://user-images.githubusercontent.com/31927590/38928035-7d2ad86c-42ff-11e8-8778-5aefe6833824.PNG)

---

### Validation:
Below are some screenshots of me implimenting validation rules for my database:

This first screenshot shows that the validation rule is; Enter a value which is not 0
![validation evidence 1](https://user-images.githubusercontent.com/31927590/39239435-cd7b712c-4878-11e8-99dd-b6b56113529c.PNG)

This second screenshot shows that the validation rule is; HP field must be greater than or equal to 100
![validation evidence 2](https://user-images.githubusercontent.com/31927590/39239437-cf0bc938-4878-11e8-88a8-b23ff91dc07b.PNG)

This third screenshot shows that the validation rule is; The Damage field has to be either 0 or greater than 100
![validation evidence 3](https://user-images.githubusercontent.com/31927590/39239497-f5023f3c-4878-11e8-8f23-134c37bd83fc.PNG)

### Forms evidence:
As you can see from the three screenshots below, i have three forms that allow me to add or update as well as delete records.

![hero form evidence](https://user-images.githubusercontent.com/31927590/39238919-63cfe326-4877-11e8-8dc1-a08ed692abf7.PNG)

![villain form evidence](https://user-images.githubusercontent.com/31927590/39238929-6d5873ae-4877-11e8-85a0-4a275a79392e.PNG)

![ability form evidence](https://user-images.githubusercontent.com/31927590/39238950-7c90805a-4877-11e8-95fb-2e50ce56e6fd.PNG)

### Reports evidence:
![hero s report evidence](https://user-images.githubusercontent.com/31927590/39238964-879fcba4-4877-11e8-84b2-f4a8075eddd0.PNG)

![villains report evidence](https://user-images.githubusercontent.com/31927590/39238977-916e07e0-4877-11e8-8171-da2e8714cc4d.PNG)

---

### SQL Code:
The code below is the SQL code that i wrote in order to create and fill my database:
```
CREATE TABLE VILLAINS(
     ID INT NOT NULL PRIMARY KEY,
     LEVEL INT NOT NULL,
     NAME VARCHAR(50) NOT NULL,
     HP FLOAT NOT NULL,
     DAMAGE FLOAT NOT NULL
     
);

CREATE TABLE HEROES(
     ID INT NOT NULL PRIMARY KEY,
     LEVEL INT NOT NULL,
     NAME VARCHAR(50) NOT NULL,
     HP FLOAT NOT NULL,
     DAMAGE FLOAT NOT NULL
);

CREATE TABLE VILLAINS_ABILITIES(
     VILLAINS_ID INT NOT NULL,
     ABILITY_ID INT NOT NULL,
     OVERALL DAMAGE FLOAT NOT NULL,
     PRIMARY KEY (VILLAINS_ID, ABILITY_ID),
     FOREIGN KEY (VILLAINS_ID) REFERENCES VILLAINS(ID),
     FOREIGN KEY (ABILITY_ID) REFERENCES ABILITIES(ID)
);

CREATE TABLE HEROES_ABILITES(
     HEROES_ID INT NOT NULL,
     ABILITY_ID INT NOT NULL,
     OVERALL DAMAGE FLOAT NOT NULL,
     PRIMARY KEY (HEROES_ID, ABILITY_ID),
     FOREIGN KEY (HEROES_ID) REFERENCES HEROES(ID),
     FOREIGN KEY (ABILITY_ID) REFERENCES ABILITIES(ID)
);

CREATE TABLE ABILITIES(
     ID INT PRIMARY KEY,
     DAMAGE FLOAT NOT NULL,
     RANGE FLOAT NOT NULL,
     NAME VARCHAR(50) NOT NULL
);

-- VILLAINS --

INSERT INTO VILLAINS VALUES(
1, 'LOKI', 1000, 3000
);

INSERT INTO VILLAINS VALUES(
2, 'KILLMONGER', 100, 500
);

INSERT INTO VILLAINS VALUES(
3, 'EGO', 5000, 5000
);

INSERT INTO VILLAINS VALUES(
4, 'HELA', 6000, 4500
);

INSERT INTO VILLAINS VALUES(
5, 'THANOS', 7000, 9999
);

INSERT INTO VILLAINS VALUES(
6, 'ULTRON', 8000, 7999
);

INSERT INTO VILLAINS VALUES(
7, 'ABOMINATION', 4999, 2999
);

-- HEROES --

INSERT INTO HEROES VALUES(
1, 'IRON MAN', 100, 4000
);

INSERT INTO HEROES VALUES(
2, 'CAPTAIN AMERICA', 200, 1000
);

INSERT INTO HEROES VALUES(
3, 'SPIDER MAN', 100, 500
);

INSERT INTO HEROES VALUES(
4, 'THOR', 1000, 2000
);

INSERT INTO HEROES VALUES(
5, 'BLACK PANTHER', 300, 1500
);

INSERT INTO HEROES VALUES(
6, 'HULK', 4000, 3000
);

INSERT INTO HEROES VALUES(
7, 'ANT MAN', 150, 1500
);

-- ABILITIES --

INSERT INTO ABILITIES VALUES(
1, 'STAFF BEAM', 500
);

INSERT INTO ABILITIES VALUES(
2, 'BLACK PANTHER', 200
);

INSERT INTO ABILITIES VALUES(
3, 'GOD POWER', 5000
);

INSERT INTO ABILITIES VALUES(
4, 'SUPERHUMAN STRENGTH', 200
);

INSERT INTO ABILITIES VALUES(
5, 'TELEKINESIS', 600
);

INSERT INTO ABILITIES VALUES(
6, 'ENERGY BEAM', 1000
);

INSERT INTO ABILITIES VALUES(
7, 'HULK STRENGTH', 600
);

INSERT INTO ABILITIES VALUES(
8, 'WEB SHOT', 100
);

INSERT INTO ABILITIES(
9, 'LIGHTENING STRIKE', 1500
);
-------------------------------
DELETE FROM VILLAINS WHERE ID<7;

DELETE FROM HEROS WHERE ID<7;

DELETE FROM ABILITIES WHERE ID<9;

DELETE FROM VILLAINS WHERE ID<7;
HP > 100

DELETE FROM HERO WHERE ID<7;
HP > 100

DELETE FROM VILLAINS WHERE ID-8;
DAMAGE > 200 AND HP < 200;

DELETE FROM HEROS WHERE ID-8;
DAMAGE > 400 AND HP < 400;
--------------------------
UPDATE HEROS
SET HP = 500
WHERE NAME LIKE 'IRON MAN';

UPDATE HEROS
SET HP = 500
WHERE NAME LIKE 'SPIDER MAN';

UPDATE HEROS
SET HP = 350
WHERE NAME LIKE 'ANT MAN';

UPDATE HEROS
SET HP = 350
WHERE NAME LIKE 'BLACK PANTHER';

UPDATE VILLAINS
SET HP = 350
WHERE NAME LIKE 'KILLMONGER';

UPDATE VILLAINS
SET HP = 4000
WHERE NAME LIKE 'ABOMINATION';

UPDATE VILLAINS
SET DAMAGE = 3500
WHERE NAME LIKE 'ABOMINATION';
-------------------------------
SELECT COUNT (*) FROM HEROS;

SELECT COUNT (*) FROM VILLAINS;

SELECT COUNT (*) FROM ABILITIES;

SELECT H.NAME, H.LEVEL, S.NAME, HS.LEVEL 

FROM HEROS H, ABILITIES S, HEROS_ABILITIES HS

WHERE HERO_ID = H.ID AND ABILITY_ID = S.ID AND H.NAME LIKE '%A%';

SELECT H.NAME, H.LEVEL, S.NAME, HS.LEVEL 

FROM VILLAINS H, ABILITIES S, VILLAINS_ABILITIES HS

WHERE VIALLAIN_ID = H.ID AND ABILITY_ID = S.ID AND H.NAME LIKE '%A%';

SELECT MAX(H.DAMAGE), MIN(H.DAMAGE) FROM HEROS H;

SELECT MAX(V.DAMAGE), MIN(V.DAMAGE) FROM VILLAINS V;
```
### Test plan:
![test plan](https://user-images.githubusercontent.com/31927590/39263036-013bbbee-48b9-11e8-88b4-7b19599b9d78.PNG)

### User and technical documentation:
#### System Overview:
My database is designed to hold specific information about the different characters in the marvel cinematic universe. The database itself has lots of different tables which consist of; Heros, villains, heros abilities, villain abilities and abilities. Each of these tables hold specific key values which relate to each character in the game. Some of the field names consist off; Name, Damage, HP, Ability, Ability damage and Overall damage. All these values within these fields can be updated at anytime if there is ever a change to the characters.
#### The role of the database system:
A database system can be used for many purposes. Most of the times a database is used for the same reason as why we are using one. To store data and information in an organised manner. Databases allow for easy access and easy management of data in real time which is what makes them so useful.
#### What is object-oriented database?
An object-oriented database is a database management system that can support the modelling and creation of data as objects. This includes the support for classes of different objects and the inheritance of class properties and methods by subclasses and their objects. When an object has been added into the database it can be referenced or called upon at a later date. You can add the object and not have to worry about adding in all the information about it straight away, so you can get all the main points in and then add the extras later if needed.
#### What is my system for?
My database has been designed to store and hold data regarding some of the characters from the marvel cinematic universe. The database was made to show the characters abilities as well as show their health and damage, so it can be compared against the others. The database will also be kept up to date to add new characters and update them if they change so it does not get outdated.
#### Risks:
When designing a database there are a few risks that you may need to look into to try and prevent:
* Reports from forms not being updated within the database meaning the data stays the same.
* Forms showing the incorrect characters and information which has not been programmed.
* Forms not loading the information from the tables.
* The tables to communicating correctly meaning that the information is not updated.
#### Contingencies:
Risks can be managed and prevented very simply by creating contingencies. Some we used were:
* Writing out all the code in a separate document and keeping it just in case anything went wrong.
* Once a line of code had been written, we would test to make sure it worked on a separate save of the database.
* Making sure that we followed the ERD so the design stays as planned.
* We made multiple saves for the database to fall back on if anything went wrong.
#### Design decisions
The overall design and how I wanted the database to be designed was all organised in the planning phase of the project. I started the design knowing that I will be creating a database for marvel characters which would include the characters and their abilities. I know from the planning stage that I would be separating the characters and abilities into completely separate tables so that they can be connected and called upon later. 

I started the design phase by creating an ERD. This ERD would help me to figure out the overall layout so that I would know what information to put in each table. The ERD also helped to establish the validations for each of the tables. The ERD may also come in handy later on when we begin to test the database. We will be able to check to make sure the relationships connect as intended. I used the user requirements to help build the ERD to make sure it fitted the requested design.

For the database I needed to make sure that it was able to hold all the data that was required for it. To start only a limited number of records were implemented to make sure it all linked together correctly and showed the data as coded. I started by making 5 tables which all held different sets of information within the records. Once all the tables were completed and set up, I then created the forms which would then bring the records from multiple tables together to show a deeper detailed version. The forms are the main thing that people are going to see as they pull all of the important information from each table to come together into an updated clear to understand form.
#### tools used:
* Microsoft Excel – Used to create the data dictionary and Test Plan
* Microsoft Access – Used to create the Database
* Draw.io – Used to create the Entity Relationship Diagram
* Microsoft word – used to create the user and technical documentation


