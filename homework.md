# SQL Homework

The Springfield Cinema is having a Marvel Movie Marathon! They have asked you to help maintain their database of movies with times and attendees.

## To access the database:

First, create a database called 'marvel'

```
# terminal
createdb marvel
```

Next, run the provided SQL script to populate your database:

```
# terminal
psql -d marvel -f marvel.sql
```

Use the supplied data as the source of data to answer the questions. Copy the SQL command you have used to get the answer, and paste it below the question, along with the result they gave.

## Questions

1.  Return ALL the data in the 'movies' table.

SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 1 | Iron Man                            | 2008 | 18:10
 2 | The Incredible Hulk                 | 2008 | 16:45
 3 | Iron Man 2                          | 2010 | 19:25
 4 | Thor                                | 2011 | 14:55
 5 | Captain America: The First Avenger  | 2011 | 13:40
 6 | Avengers Assemble                   | 2012 | 18:10
 7 | Iron Man 3                          | 2013 | 18:30
 8 | Thor: The Dark World                | 2013 | 16:50
 9 | Batman Begins                       | 2005 | 21:25
10 | Captain America: The Winter Soldier | 2014 | 12:05
11 | Guardians of the Galaxy             | 2014 | 14:00
12 | Avengers: Age of Ultron             | 2015 | 16:30
13 | Ant-Man                             | 2015 | 12:35
14 | Captain America: Civil War          | 2016 | 20:40
15 | Doctor Strange                      | 2016 | 21:50
16 | Guardians of the Galaxy 2           | 2017 | 19:20
17 | Spider-Man: Homecoming              | 2017 | 13:50
18 | Thor: Ragnarok                      | 2017 | 21:50
19 | Black Panther                       | 2018 | 19:30
(19 rows)

2.  Return ONLY the name column from the 'people' table

SELECT name FROM people;

name        
--------------------
Andrew Gray
Andrew Kirkwood
Andrew Wyper
Catherine Hall
Cosy Abott
Evan Smith
Gary Clark
James Fraser
James Smith
Jamie Ryan
Jen Merritt
Lauren Brett
Luca Sanz Charreun
Matteo Fusillo
Olivia Wright
Patrick ONeill
Ross Cumming
Sigurd Watt
Silvia Simonassi
Stephen Ramsay
Steve Vance
(21 rows)

3.  Oops! Someone spelled Cody Abbott's name wrong! Change it to reflect the proper spelling.

UPDATE people SET name = 'Cody Abott' WHERE name = 'Cosy Abott';
SELECT name FROM people;

name        
--------------------
Andrew Gray
Andrew Kirkwood
Andrew Wyper
Catherine Hall
Evan Smith
Gary Clark
James Fraser
James Smith
Jamie Ryan
Jen Merritt
Lauren Brett
Luca Sanz Charreun
Matteo Fusillo
Olivia Wright
Patrick ONeill
Ross Cumming
Sigurd Watt
Silvia Simonassi
Stephen Ramsay
Steve Vance
Cody Abott
(21 rows)

4.  Return ONLY Olivia Wright's name from the 'people' table.

SELECT name FROM people WHERE name = 'Olivia Wright';

name      
---------------
Olivia Wright
(1 row)

5.  The cinema is showing 'Batman Begins', but Batman is DC, not Marvel! Delete the entry from the 'movies' table.

DELETE FROM movies WHERE title = 'Batman Begins';
SELECT title FROM movies;

title                
-------------------------------------
Iron Man
The Incredible Hulk
Iron Man 2
Thor
Captain America: The First Avenger
Avengers Assemble
Iron Man 3
Thor: The Dark World
Captain America: The Winter Soldier
Guardians of the Galaxy
Avengers: Age of Ultron
Ant-Man
Captain America: Civil War
Doctor Strange
Guardians of the Galaxy 2
Spider-Man: Homecoming
Thor: Ragnarok
Black Panther
(18 rows)

6.  We forgot one of the main characters! Add Chris Fraser to the 'people' table

INSERT INTO people (name) VALUES ('Chris Fraser');
SELECT name FROM people;

name        
--------------------
Andrew Gray
Andrew Kirkwood
Andrew Wyper
Catherine Hall
Cosy Abott
Evan Smith
Gary Clark
James Fraser
James Smith
Jamie Ryan
Jen Merritt
Lauren Brett
Luca Sanz Charreun
Matteo Fusillo
Olivia Wright
Patrick ONeill
Ross Cumming
Sigurd Watt
Silvia Simonassi
Stephen Ramsay
Steve Vance
Chris Fraser
(22 rows)

7.  John Smith has decided to hijack our movie evening, Remove him from the table of people.

DELETE FROM people WHERE name = 'James Smith';
SELECT name FROM people;

name        
--------------------
Andrew Gray
Andrew Kirkwood
Andrew Wyper
Catherine Hall
Cosy Abott
Evan Smith
Gary Clark
James Fraser
Jamie Ryan
Jen Merritt
Lauren Brett
Luca Sanz Charreun
Matteo Fusillo
Olivia Wright
Patrick ONeill
Ross Cumming
Sigurd Watt
Silvia Simonassi
Stephen Ramsay
Steve Vance
(20 rows)

8.  The cinema has just heard that they will be holding an exclusive midnight showing of 'Avengers: Infinity War'!! Create a new entry in the 'movies' table to reflect this.

``INSERT INTO movies (title, year, show_time) VALUES ('Avengers: Infinity War', 2018, '00:00');
SELECT title FROM movies;``

```title                
-------------------------------------
Iron Man
The Incredible Hulk
Iron Man 2
Thor
Captain America: The First Avenger
Avengers Assemble
Iron Man 3
Thor: The Dark World
Batman Begins
Captain America: The Winter Soldier
Guardians of the Galaxy
Avengers: Age of Ultron
Ant-Man
Captain America: Civil War
Doctor Strange
Guardians of the Galaxy 2
Spider-Man: Homecoming
Thor: Ragnarok
Black Panther
Avengers: Infinity War
(20 rows)
```
9.  The cinema would like to make the Iron Man movies a triple billing. Find out the show time of "Iron Man 2" and set the show time of "Iron Man 3" to start two hours later.

SELECT title, show_time FROM movies WHERE title = 'Iron Man 2';
UPDATE movies SET show_time = '21:25' WHERE title = 'Iron Man 3';
SELECT title, show_time FROM movies;

title    | show_time
------------+-----------
Iron Man 2 | 19:25
(1 row)

UPDATE 1
             title                | show_time
-------------------------------------+-----------
Iron Man                            | 18:10
The Incredible Hulk                 | 16:45
Iron Man 2                          | 19:25
Thor                                | 14:55
Captain America: The First Avenger  | 13:40
Avengers Assemble                   | 18:10
Thor: The Dark World                | 16:50
Batman Begins                       | 21:25
Captain America: The Winter Soldier | 12:05
Guardians of the Galaxy             | 14:00
Avengers: Age of Ultron             | 16:30
Ant-Man                             | 12:35
Captain America: Civil War          | 20:40
Doctor Strange                      | 21:50
Guardians of the Galaxy 2           | 19:20
Spider-Man: Homecoming              | 13:50
Thor: Ragnarok                      | 21:50
Black Panther                       | 19:30
Iron Man 3                          | 21:25
(19 rows)



## Extension

1.  Research how to delete multiple entries from your table in a single command.

DELETE FROM movies WHERE title IN (('Iron Man'), ('Iron Man 2'));
SELECT * FROM movies;

id |                title                | year | show_time
----+-------------------------------------+------+-----------
 2 | The Incredible Hulk                 | 2008 | 16:45
 4 | Thor                                | 2011 | 14:55
 5 | Captain America: The First Avenger  | 2011 | 13:40
 6 | Avengers Assemble                   | 2012 | 18:10
 7 | Iron Man 3                          | 2013 | 18:30
 8 | Thor: The Dark World                | 2013 | 16:50
 9 | Batman Begins                       | 2005 | 21:25
10 | Captain America: The Winter Soldier | 2014 | 12:05
11 | Guardians of the Galaxy             | 2014 | 14:00
12 | Avengers: Age of Ultron             | 2015 | 16:30
13 | Ant-Man                             | 2015 | 12:35
14 | Captain America: Civil War          | 2016 | 20:40
15 | Doctor Strange                      | 2016 | 21:50
16 | Guardians of the Galaxy 2           | 2017 | 19:20
17 | Spider-Man: Homecoming              | 2017 | 13:50
18 | Thor: Ragnarok                      | 2017 | 21:50
19 | Black Panther                       | 2018 | 19:30
(17 rows)
