---
title: "Problems with mysql and mythtv"
date: 2006-09-15
forum: Desktop Environments
---

### Post by drews_blunted on 2006-09-15
Hello, i have been trying very hard to get mythtv intalled on my dapper install. I just can not seem to get mysql to work correctly, atleast thats what i think is the problem, i get this error when i try and run the myth-tv install. So far i have installed mysql and all the myth tv packaged plus lots and lots of extra packages that all these tutorials i have have looked at on google have told me. 

Ive already Googled and tryed following atleast 6 tutorials all with me having some sort of problem getting it to work. 

I get the below error. 


QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-09-15 18:49:42.835 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-09-15 18:49:42.891 Database not open while trying to load setting: RunFrontendInWindow
2006-09-15 18:49:43.204 Unable to connect to database!
2006-09-15 18:49:43.204 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-09-15 18:49:43.210 Joystick disabled.
QSqlQuery::exec: database not open
2006-09-15 18:49:43.259 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-09-15 18:49:43.316 Unable to connect to database!
2006-09-15 18:49:43.316 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

QSqlQuery::exec: database not open
QSqlQuery::exec: database not open
2006-09-15 18:49:43.371 DB Error (KickDatabase):
Query was:
SELECT NULL;
No error type from QSqlError?  Strange...
2006-09-15 18:49:43.428 Unable to connect to database!
2006-09-15 18:49:43.428 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)


If anyone know how to get myth tv installed and working well, could you please respond and help me figure out whet im doing wrong? ](*,)

---

### Post by NutrOn on 2006-09-17
Here is my problem if anyone is tracking these.
I'm also not clear as to what user and password I'm supposed to be setting, root?
Not an answer to the first post (my apologies) just hoping some guru comes along.
2006-09-17 21:08:04.887 Database not open while trying to save setting: Language2006-09-17 21:08:04.888 Unable to connect to database!
2006-09-17 21:08:04.888 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'lewis'@'localhost' (using password: YES)

2006-09-17 21:08:31.621 Writing settings file /home/lewis/.mythtv/mysql.txt
2006-09-17 21:08:31.844 Unable to connect to database!
2006-09-17 21:08:31.845 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'lewis'@'localhost' (using password: YES)

---

### Post by terotil on 2006-11-21
You might just want to check what db settings (that is what mysql.txt) mythbackend reads on startup.  I had working myth-configuration and one day I restarted backend and it would not start.  I had the very same "access denied".  The reason was that for some odd reason mythbackend did not read /etc/mythtv/mysql.txt but /home/terotil/.mythtv/mysql.txt which happened to be clean example mysql.txt and had empty password.  Removing the /home/terotil/.mythtv/mysql.txt resolved the problem.

You could also be missing db access grants or some packages, see
[http://www.smorgasbord.net/problems_with_mysql_and_mythtv](http://www.smorgasbord.net/problems_with_mysql_and_mythtv)

---

### Post by rvickers on 2006-11-21
Download phymyadmin via synaptic, Enter [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) in your browser, login as root & no password and configure mysql from there.
Good Luck...

---

### Post by superm1 on 2006-11-21
> **terotil said:**
> You might just want to check what db settings (that is what mysql.txt) mythbackend reads on startup.  I had working myth-configuration and one day I restarted backend and it would not start.  I had the very same "access denied".  The reason was that for some odd reason mythbackend did not read /etc/mythtv/mysql.txt but /home/terotil/.mythtv/mysql.txt which happened to be clean example mysql.txt and had empty password.  Removing the /home/terotil/.mythtv/mysql.txt resolved the problem.

You could also be missing db access grants or some packages, see
[http://www.smorgasbord.net/problems_with_mysql_and_mythtv](http://www.smorgasbord.net/problems_with_mysql_and_mythtv)

If you are spawning mythtv as a regular user and not the user "mythtv", this is why this would happen.  

Start mythbackend from the init script
```
sudo /etc/init.d/mythtv-backend start
```

---

