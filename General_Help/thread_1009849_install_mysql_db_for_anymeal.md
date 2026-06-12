---
title: "install mysql db for anymeal"
date: 2008-12-13
forum: General Help
---

### Post by ndefontenay on 2008-12-13
Good morning,

I've installed anymeal and try to get the mysql database to work. I get this:

Installing MySQL system tables...
Installation of system tables failed!
Examine the logs in /home/nicolas/.kde/share/apps/anymeal/madb for more information.
You can try to start the mysqld daemon with:
/usr/sbin/mysqld --skip-grant &
and use the command line tool
/usr/bin/mysql to connect to the mysql
database and look at the grant tables:
shell> /usr/bin/mysql -u root mysql
mysql> show tables
Try 'mysqld --help' if you have problems with paths. Using --log
gives you a log in /home/nicolas/.kde/share/apps/anymeal/madb that may be helpful.
The latest information about MySQL is available on the web at
[http://www.mysql.com](http://www.mysql.com)
Please consult the MySQL manual section: 'Problems running mysql_install_db',
and the manual section that describes problems on your OS.
Another information source is the MySQL email archive.
Please check all of the above before mailing us!
And if you do mail us, you MUST use the /usr/bin/mysqlbug script!
p??p??

I've found a similar thread unanswered with exactly the same error.

Anybody has an idea of what could go wrong?

I've checked the directory /home/nicolas/.kde/share/apps/anymeal/madb for logs it's totally empty.

Nico

---

