---
title: "Install lamp webserver on ubuntu"
date: 2009-03-07
forum: General Help
---

### Post by smooch101 on 2009-03-07
Install Lamp Php, Mysql , Apache2 On Ubuntu
I have tested this guide on ubuntu 8.04 and up however it should work on others
We are using the terminal to install our lamp system

Install Apache2:

sudo apt-get install apache2

Once it is installed you can use:

sudo /etc/init.d/apache2 start

or to stop
sudo /etc/init.d/apache2 stop

Your website files are located in /var/www/

Install Php:

sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

Then Create A Php File
sudo gedit /var/www/test.php 
Then Type In
< ?php echo “Hello World”; ?> 

Now open firefox and type:
[http://localhost/test.php](http://localhost/test.php)

Install Mysql:

sudo apt-get install mysql-server 

Then Restart Apache and your done.

---

### Post by smooch101 on 2009-03-07
> **smooch101 said:**
> Install Lamp Php, Mysql , Apache2 On Ubuntu
I have tested this guide on ubuntu 8.04 and up however it should work on others
We are using the terminal to install our lamp system

Install Apache2:

sudo apt-get install apache2

Once it is installed you can use:

sudo /etc/init.d/apache2 start

or to stop
sudo /etc/init.d/apache2 stop

Your website files are located in /var/www/

Install Php:

sudo apt-get install php5 libapache2-mod-php5
sudo /etc/init.d/apache2 restart

Then Create A Php File
sudo gedit /var/www/test.php 
Then Type In
< ?php echo “Hello World”; ?> 

Now open firefox and type:
[http://localhost/test.php](http://localhost/test.php)

Install Mysql:

sudo apt-get install mysql-server 

Then Restart Apache and your done.

Please do not copy this guide.

---

### Post by DGortze380 on 2009-03-07
FYI: You can install a LAMP by default along your base system install if you use a server install disk. Just harden the install and you're done.

---

### Post by Iowan on 2009-03-07
**tasksel install lamp-server** is another option.

> **smooch101 said:**
> Please do not copy this guide.Is that a copyright notice?

---

