---
title: "Serious trouble installing MySQL on Breezy"
date: 2005-12-18
forum: General Help
---

### Post by TmP on 2005-12-18
Hi!

I'm having serious trouble instaling a combination of 
Apach2/PHP4/MySQL4

I've been trying to install it following the Wiki:
[https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28MySQL%29](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28MySQL%29)

Apache and PHP runs fine but MySQL doesn't

It's a matter that has been discussed earlyer, in the times of Wharty, but never seemed to be resolved.

Here's what I get when I try to install MySQL after installing apache2 and php4

Configuring mysql-server (4.0.24-10ubuntu2) ...
Stopping MySQL database server: mysqld.

WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

So what should I do?

---

### Post by greenway on 2005-12-18
Sounds like your problem is not installing MYSQL but getting the deamon to run. Did you already take a look at your syslog?

---

### Post by TmP on 2005-12-18
I would love to but I'm not sure how.

---

### Post by TmP on 2005-12-18
This is what I get when trying to set up a root password
or call mysqld

tempest@tempest:/usr$ mysql -u root
ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

And altough apt-get believes MySQL is installed, the only content of /etc/mysql is 
debian.cfg with the following text

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = yGTUY5tNfQRm50DC
socket   = /var/run/mysqld/mysqld.sock

---

### Post by TmP on 2005-12-18
This is what the Ubuntu Wiki suggests to install:
sudo apt-get install apache2
-> procedes fine
sudo apt-get install php4
-> goes well
sudo apt-get install mysql-server

and here's what I get


Stopping MySQL database server: mysqld.

WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.
Starting MySQL database server: mysqld...failed.
        Please take a look at the syslog.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

No wonder it can't find /etc/mysql/my.cnf
It's supposed to install it first
Yet the whole /etc/mysql is empty
And i don't know how to check the logs...

---

### Post by greenway on 2005-12-18
Open a terminal and go to "/var/log", this is where you will find all of your system's logs. You might want to take a look at syslog for your entire system's log. You could also look at deamon.log. 

Maybe it really didn't install ok. You could try downloading the package yourself and install it using dpkg.

---

