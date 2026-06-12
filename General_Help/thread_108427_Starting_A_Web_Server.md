---
title: "Starting A Web Server"
date: 2005-12-26
forum: General Help
---

### Post by psychotoxic on 2005-12-26
I need help i would like to host an apache webserver but i need to know what files to install it must have php mysql etc 
When i look through the add aplications i see apache and all the other file but i dont now what to install please i could really use the help and im a noob so please explain in detail

---

### Post by modular9 on 2005-12-26
I used this "how to" to setup a server ( not very secure- at leas the way i set it up ) on hoary, just installed breezy so will have to do it all again 

[http://ubuntuforums.org/showthread.php?t=17875](http://ubuntuforums.org/showthread.php?t=17875) 

it was easy to do and at the end of it i had a testing server with php mysql phpmyadmin apache didnt need nor want the webmin thing so i ditched that step. 

Cheers

---

### Post by Cyril on 2005-12-26
I happen to have those 3 things installed.  I can tell you what packages  I have installed.

apache2
apache2-common
apache2-mpm-prefork
apache2-utils
mysql-common-4.1
mysql-server-4.1
mysql-client-4.1
php5-mysql
php5
php5-cgi
php5-common

I can't remember exactly the steps I took in installing these packages but they started working without me doing any configuration.

---

### Post by psychotoxic on 2005-12-26
[QUOTE=Cyril]I happen to have those 3 things installed.  I can tell you what packages  I have installed.

apache2
apache2-common
apache2-mpm-prefork
apache2-utils
mysql-common-4.1
mysql-server-4.1
mysql-client-4.1
php5-mysql
php5
php5-cgi
php5-common

I can't remember exactly the steps I took in installing these packages but they started working without me doing any configuration.[/QUOTE]


Thanks i try and install them 1 more question i am behind a router will this cause any problem for me also i have DMZ enabled for the pc im going to use for this

---

### Post by GuitarFingers on 2005-12-26
These instructions are for the latest versions of php, mysql and apache that are available for ubuntu.

If you are using Synaptic to install the packages you will need to select the following files:

Firstly, choose apache2. This will automatically select the other files needed to get apache running.

For mysql support choose mysql-server-4.1. Again, other files required will be added (or removed).

Lastly php5 and php5-mysql are what you need to get php functionality.

Once you have installed these the webserver and mysql will start automatically.  You can locate the webserver at [http://localhost/apache2-default](http://localhost/apache2-default) and the disc location is /var/www/apache2default.

I also install the mysql-admin front end for easy maintenance of the database.

This will get your web server up and running but NOTE there is no security here! Its fine for a local install where you may be testing things but you will need to delve a bit deeper (try searching these forums and the net) for information on improving security if you are going to expose this server to the great masses on the internet.

If you would like to test php functionality just place a file called test.php in the apache root directory (/var/www/apache2-default)with the following line in it:

<? phpinfo() ?>

Going to [http://localhost/apache2-default/test.php](http://localhost/apache2-default/test.php) will give you lots of information.

Hope that helps, private message me if you need any more assistance.

GuitarFingers

---

### Post by psychotoxic on 2005-12-26
thanks for the help

---

### Post by psychotoxic on 2005-12-26
Mysql Help how do i login to mysql i have phpmyadmin and mysql administrator installed but i need to login into it i dont no the password

---

### Post by psychotoxic on 2005-12-26
[QUOTE=psychotoxic]Mysql Help how do i login to mysql i have phpmyadmin and mysql administrator installed but i need to login into it i dont no the password[/QUOTE]
nevermind i got it thanks any way

---

### Post by psychotoxic on 2005-12-26
When ever i try and add a file or folder to the webserver it says i dont have permission

---

### Post by paddyg on 2005-12-26
[QUOTE=psychotoxic]When ever i try and add a file or folder to the webserver it says i dont have permission[/QUOTE]
if you mean adding new folders to the document root (/var/www), in terminal just
```
sudo mkdir /var/www/newsite
sudo chown user:user /var/www/newsite 

```

---

### Post by psychotoxic on 2005-12-26
no when i try to copy a folder from the desktop or rename a file it doesnt give me permission i mean how can i not have permission how do i get it

---

### Post by dcraven on 2005-12-26
Your best bet might be to put your website in ~/public_html, then you won't have any permissions problems. You can access your site by going to [http://yourserver.org/~youruser/](http://yourserver.org/~youruser/) in your browser.

HTH,
~djc

---

### Post by sudharshan on 2005-12-26
also make sure your web pages are locate outside the default htdocs directory..this can be done by modifying the httpd.conf

---

