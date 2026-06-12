---
title: "I am learning PHP and MySQL, Got an error on MySQL Method"
date: 2007-07-09
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2007-07-09
Hi All,

I could not able to get the result when I use methods for connecting to database in PHP script. 

I installed PHP and MySQL from Sympatetic package manager.

It complaint the method donot exists.

I was using Ubuntu linux and Installed MySQL and PHP through sympathitic.

Please let me know if I miss any configuration.

Check the site below 

[http://www.w3schools.com/php/php_mysql_connect.asp](http://www.w3schools.com/php/php_mysql_connect.asp)

I am getting the error at mysql_connect()

It says the method doesn't exists.


Thanks in advance.

Regards,

Swaroop Kunduru.

---

### Post by scragar on 2007-07-09
by the sounds of it PHP isn't picking up MySQL, you could try re-installing it, but I'm not sure if that would fix it, personaly I uninstalled apache, PHP and MySQL after a few dificulties and went with Lampp from apachefriends.org

---

### Post by jmazzarelli on 2007-07-09
Make sure you have a mysql extension:
```
php -m | grep mysql
```
If not, try:
```
sudo apt-get install php5-mysql
```

---

### Post by GWoitena on 2007-07-09
Try this:

$db = mysql_connect("localhost", "root");
mysql_select_db("the name of your mysql db", $db);

You're not telling mysql which database to connect to.  You need to do this even if mysql has only one db in it.

on edit---------->

in the  mysql_connect string, use whatever user name and password you're using to connect.  I believe the mysql_select_db string is just as important as the first part.

---

### Post by scragar on 2007-07-10
> **GWoitena said:**
> Try this:

$db = mysql_connect("localhost", "root");
mysql_select_db("the name of your mysql db", $db);

You're not telling mysql which database to connect to.  You need to do this even if mysql has only one db in it.

on edit---------->

in the  mysql_connect string, use whatever user name and password you're using to connect.  I believe the mysql_select_db string is just as important as the first part.
this worthless, unless you can connect then it doesn't matter if you can select the DB, you can't do anything with it. Of course once the connection problem is fixed your point falls back into validity.

---

