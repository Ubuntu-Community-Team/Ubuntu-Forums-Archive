---
title: "MythTV,"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Keith_Beef on 2006-09-19
I'm having trouble setting up MythTV to work on Ubuntu 6.06.

I installed the packages today. Some message flashed by in Synaptic, about "dpkg -reconfigure -force", but too fast for me to note it down.

So, here's what happens in my terminal window:

> $ gksudo mythtv-setup
2006-09-19 12:46:07.226 New DB connection, total: 1
2006-09-19 12:46:07.244 Unable to connect to database!
2006-09-19 12:46:07.244 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

Total desktop width=1280, height=1024, numscreens=1
2006-09-19 12:46:07.247 Unable to connect to database!
2006-09-19 12:46:07.247 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

...big snip...

2006-09-19 12:46:23.951 Unable to connect to database!
2006-09-19 12:46:23.951 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

2006-09-19 12:46:23.951 Failed to init MythContext, exiting.

There is this database error for each time mythtv-setup tried to set a parameter.

I have MySQL 5.0.22 installed, and MythTV Database 0.18.1 was installed with MythTV.

Anybody know what I can do to fix this?

Beef.

---

### Post by tagra123 on 2006-09-19
I haven't upgraded from breezy on the mythtv system -- mainly because erverything including nuvexport is working correctly.

This link may help

[http://www.abarbaccia.com/content/view/17/32/](http://www.abarbaccia.com/content/view/17/32/)

check this section for mysql problems

Install mysql

    $  sudo apt-get install mysql-server

Assign root password:

    $  mysql -u root mysql
    UPDATE user SET Password=PASSWORD('<your password here>') WHERE user='root';
    FLUSH PRIVILEGES;
    quit

---

### Post by Keith_Beef on 2006-09-19
That's great! Thanks.

From your reply, I was able to connect to the MySQL server and start the mysql-admin tool.

Unfortunately, that's as far as I've got for now. The mysql-admin tool seems to hang when I try "User Administration".

When we're talking about a "user" in discussions about MySQL, is this the same as a user declared in /etc/passwd or is it a separate sort of user known only to MySQL?

Beef.

---

### Post by tagra123 on 2006-09-19
I believe I used root as the root password and my regular password to log in with just to make it easier to remember.

Then later on you issue a similar command to add the mythtv user with mythtv as the password.

---

### Post by Simon80 on 2006-09-22
> **Keith_Beef said:**
> That's great! Thanks.

From your reply, I was able to connect to the MySQL server and start the mysql-admin tool.

Unfortunately, that's as far as I've got for now. The mysql-admin tool seems to hang when I try "User Administration".

When we're talking about a "user" in discussions about MySQL, is this the same as a user declared in /etc/passwd or is it a separate sort of user known only to MySQL?

Beef.
MySQL users are separate.  Also, see [https://launchpad.net/distros/ubuntu/+source/mysql-admin/+bug/29802](https://launchpad.net/distros/ubuntu/+source/mysql-admin/+bug/29802) about the hang.

---

