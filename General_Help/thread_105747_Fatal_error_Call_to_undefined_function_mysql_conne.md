---
title: "Fatal error: Call to undefined function: mysql_connect()"
date: 2005-12-19
forum: General Help
---

### Post by slempl on 2005-12-19
In problems again...
everything works perfectly mysql, apache, php

PHP Version 4.4.0-3

apache 2

MySQL 4.0.24_Debian-10ubuntu2-log

 phpMyAdmin 2.6.4-pl1-Debian-1ubuntu1


And i keep getting a message 

Fatal error: Call to undefined function: mysql_connect() in /var/www/forinpro/diff/db.php on line 5

This is my code...


<?
$db_server = "localhost";
$db_database = "forinpro";

$db = mysql_connect($db_server,"","") or die("ERROR CONNECTING TO: ".$db_server."<br>".mysql_error());
mySql_select_db($db_database,$db) or die("COULD NOT SELECT DATABASE: ".$db_database."<br>".mysql_error());

?>

HELP!:(

---

### Post by duminas on 2005-12-19
Install the *php4-mysql* package--this will add MySQL functionality to your PHP4 install.

A lot of PHP functions can be added or removed in this manner. As you are using php 4, you only want the **php4-*** packages.

A few examples for you are:
php4-pgsql - PostgreSQL module.
php4-sybase - MSSQL module.
php4-xslt - XSLT (XML stylesheets) module.

If you use Synaptic, just do a search and issue "php4-" (no quotes) to get a list of them.

---

### Post by slempl on 2005-12-19
root@zverka:/home/sergio# apt-get install php4-mysql
Reading package lists... Done
Building dependency tree... Done
php4-mysql is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



It's allready there....  :(

---

### Post by duminas on 2005-12-19
This is irrelevant, but:
```
mySql_select_db...
```
should probably be:
```
mysql_select_db...
```
As to your MySQL issue, a quick question. Can you try restarting Apache? If you do not know how, issue the following on the terminal:
```
sudo /etc/init.d/apache2 restart
```
You can probably drop the "sudo" if you're running a terminal as root. Maybe it needed to propogate changes?

---

### Post by slempl on 2005-12-19
Allready tried that... nothing helps!   :(

---

### Post by duminas on 2005-12-19
Tried the phpinfo test yet?
If you don't know what this is, make a file called "info.php" in your web-accessible folder, and in it, put this (and only this):
[php]<?php phpinfo(); ?>[/php]Then search this for a MySQL section.
I can't think of what's borking it.

**EDIT:** What... the hell? This is odd--I'm getting that exact same error. PHPMyAdmin can connect and do its things perfectly fine, but *none* of my other scripts are working.

---

### Post by slempl on 2005-12-19
Tried that too but all i get from it about mysql is this:



dbx
dbx support 	enabled
dbx version 	1.0.0
supported databases 	MySQL ODBC PostgreSQL Microsoft SQL Server FrontBase Oracle 8 (oci8) Sybase-CT


I've ctrl+f (mysql) that is all i've got from it...

---

### Post by duminas on 2005-12-19
What bugs me to no end is that PHPMyAdmin functions perfectly, but nothing else does. I can't find where PMA is creating its DB connection, either.

This might not help, but [apparently using PHP5 instead solves the problem](http://www.ubuntuforums.org/showthread.php?t=97154&highlight=php4+mysql).

---

### Post by slempl on 2005-12-19
Yes.... but is it possible to use old php4 functions in pfp5?..... because my job mates and me use php4 and we have made templeates wich i could not use if i install php5 i'm the only one running ubuntu machine... and so on....

Should i reinstall phpmyadmin?

---

### Post by duminas on 2005-12-19
You should be able to do most things you could do with PHP4 in PHP5--I know some things got changed in 5, but not sure as to what.

And I never used the PHPMyAdmin from the repositories. As those likely install to /var/www (my webroot's not there), they'd not work for me. Instead, I just went to [PHPMyAdmin's homepage](http://www.phpmyadmin.net/home_page/), downloaded the archive there, and dumped it into my webroot. Worked a charm.

---

### Post by slempl on 2005-12-19
I've just tried dumping phpmyadmin folder that i've downloaded from their web page... info.php is the same! don't know what to do more... how to uninstall phpmyadmin that ive got from thre repositores?....

---

### Post by duminas on 2005-12-19
info.php wouldn't be changing. What I mean is that PHPMyAdmin doesn't seem to use the traditional mysql_connect() function--they're using something else, which is likely why it is working. This is the issue that was baffling me.

As for removing the one from the repos, just go *apt-get remove phpmyadmin*, I believe.

---

### Post by tjhanschke on 2005-12-20
I am getting the exact same error -- I tried removing and re-installing all the packages of php (php4, php4-mysql, php5, php5-mysql, etc.) and restarting apache2 after each instance.

I'm completely baffled...

The only code I'm trying to pass is:
<?php
mysql_connect();
?>

And I receive this in return:

"Fatal error: Call to undefined function mysql_connect() in /var/www/apache2-default/index.php on line 2"

---

### Post by imbunche on 2005-12-27
Hi,
just struggle with the same problem for a couple of hours.
The solution was to uncomment the line :

extension=mysql.so

in /etc/php4/apache2/php.ini

Hope that helps

---

### Post by RobertLos on 2006-01-11
uncommenting the line

extension=mysql.so

is definitely the solution. I had the same problem. Now it works

---

### Post by garner_nc on 2006-05-10
It's still not working for me. I tried uncommenting  the 

extension=mysql.so

in my php,ini file and restarting the Apache server. 

No help.

All the Best,
Doug White

---

### Post by juliakm on 2007-02-09
Thanks for all of the tips. I got mysql to work for php5 by uncommenting extension=mysql.so in php.ini and then restarting Apache with: 

sudo /etc/init.d/apache2 restart

Julia

---

### Post by bernardfrancois on 2007-09-10
Thanks, that solution worked for me too!

---

### Post by acidsolution on 2008-01-25
Thanks a lot 
adding the line 
extension=mysql.so
worked out for me it was really a life saver..:):)

---

