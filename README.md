# sql-query-practice


### Round 1

Connect to the LikeyPix database in Beekeeper, and answer the following questions:

1. Write a query that returns all Users

```
Paste your query below:

select * from users;

```

2. Write a query that returns all Posts

```
Paste your query below:

select * from posts;

```

3. Write a query that returns the count of all Posts

```
Paste your query below:

select count(*) from posts;

```

4. Which Post had the most Comments?

Answer: post_id: 1 has 3 comments

5. Write a query that returns the Post which had the least Comments

```
Paste your query below:

select count(*) as total_comments, post_id from comments
	group by post_id
    order by total_comments asc
    limit 1;

```

6. Which User has the most Comments?

Answer: user_id: 1 had the most comments with 3

7. Write a single query to get all of the Posts and their Comments (You'll see the same Post repeated in the results)

```
Paste your query below:

select p.id, p.url, c.comment
from posts p inner join comments c
	on p.id = c.post_id;

```

### Round 2

- Disconnect from the `likeypix` database connection
- Connect to the `classroom` database connection

1. Write a query to get the first name, last name, and github URL for every Student in the `students` table

```
Paste your query below:

select s.first_name, s.last_name, s.github_url from students s;

```

2. Write a query to get a list of Students who do not have a LinkedIn URL

```
Paste your query below:

select *
from students s
where length(s.linkedin_url) > 0;

```

3. Write a query to get a list of Teachers with the "Teaching Assistant" Role

```
Paste your query below:

select * from teachers t where t.teacher_role_id = 2;

```

4. Write a query to get a list of Students, and their Class' `slug`

```
Paste your query below:

select s.first_name, s.last_name, c.name
	from students s
    inner join classes c
    	on s.class_id = c.id;

```

5. Write a query to get the length of every students First Name

```
Paste your query below:

select s.first_name, length(s.first_name) from students s;

```

6. What is the ID of the Student with the longest Last Name?

Answer: student.id: 7 - Christopher

7. Write a query to get a list of Students in reverse alphabetical order of First Name

```
Paste your query below:

select * from students
	order by students.first_name desc;

```

### Round 3

- Disconnect from the `classroom` database connection
- Connect to the `food` database connection

This Round is going to require you to get curious about your surroundings. At some point in your path as a developer, you will work on a project that already has an existing database. That database may be quite old, or have been built on a different set of standards.

These questions will be focused on exploring an unknown database that does not follow the standards we have established in class. See if you can work out answers to the following questions:


1. What table contains information about individual food items? 

Answer: food_des

2. Using the table from the previous answer as your starting point - what table do you think contains Food Group information about individual foods?

Answer: fd_group

3. Write a query to get the name of a food, and its corresponding food group name 

```
Paste your query below:

select fd.ndb_no, fd.shrt_desc, fdg.fddrp_desc
	from food_des fd
		inner join fd_group fdg
    	on fd.fdgrp_cd = fdg.fdgrp_cd
    where fd.ndb_no::integer = 01001;

```

4. Identify the table that has information about data sources

Answer: data_src

5. Using the table from your previous answer, write a query that will get the oldest data source

```
Paste your query below:

select * from data_src
	order by year asc
    limit 1;

```

6. How many foods contain "Egg" in their description?

Answer: 101

7. Write a query that will return a count of foods in each food group

```
Paste your query below:

select f.fdgrp_cd, count(*) as total from food_des f
	group by f.fdgrp_cd
    order by total desc;

```
