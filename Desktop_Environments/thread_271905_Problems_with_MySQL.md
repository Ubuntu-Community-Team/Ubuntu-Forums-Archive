---
title: "Problems with MySQL"
date: 2006-10-05
forum: Desktop Environments
---

### Post by hraposo on 2006-10-05
I installed MySQL but
when I do ```
mysql -h localhost -u helder -p123123
``` the output is ```
ERROR 1045: Access denied for user: 'helder@localhost' (Using password: YES)
``` Why?

---

### Post by hraposo on 2006-10-05
another problem: When I install MySQL appears the menssage at the end > Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
 And I've not the **mysqld.sock**

---

### Post by hraposo on 2006-10-05
Last problem solved. But still the first problem!

---

### Post by procras on 2006-10-05
Have you set up the administrator password?

Remember users on your system are different from users for Mysql

You need to create users in Mysql using something like the GRANT statement
from the mysql monitor.

Search for Mysql Administrator password to create the root user then

$ mysql -u root -p
And type in your password at the prompt
If that works then try something like
mysql > CREATE database mydatabase;
mydql > GRANT ALL ON mydatabase.* to helder@localhost IDENTIFIED BY "secretpassword"

Or something similar

Good luck

---

