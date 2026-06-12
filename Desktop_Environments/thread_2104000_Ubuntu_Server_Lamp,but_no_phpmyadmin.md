---
title: "Ubuntu Server Lamp,but no phpmyadmin?"
date: 2013-01-11
forum: Desktop Environments
---

### Post by BStrizzy on 2013-01-11
Hey guys,

I installed LAMP on my ubuntu server not to long ago, and I am trying to make a wordpress site for it, and to do so I need access phpmyadmin and for some reason when I go to my browser and enter 

"my ip"/phpmyadmin 

i get 
**Not Found**

 The requested URL /phpmyadmin was not found on this server.
  Apache/2.2.14 (Ubuntu) Server at 192.168.x.x Port 80


advice?

---

### Post by iponeverything on 2013-01-11
> **BStrizzy said:**
> 


advice?

yes, google and look the documentation.

---

### Post by lisati on 2013-01-11
AFAIK phpmyadmin doesn't get installed as part of a "standard" LAMP installation. 

I've found that the services provided by installing webmin instead usually meet my needs, including several of the tasks that one would use phpmyadmin for.

---

### Post by BStrizzy on 2013-01-12
> **lisati said:**
> AFAIK phpmyadmin doesn't get installed as part of a "standard" LAMP installation. 

I've found that the services provided by installing webmin instead usually meet my needs, including several of the tasks that one would use phpmyadmin for.

ok i tried the apt-get install phpmyadmin and it says its already installed

---

### Post by CharlesA on 2013-01-12
Purge phpmyadmin and reinstall it.

```
sudo apt-get purge phpmyadmin && sudo apt-get install phpmyadmin
```

Be sure to select the correct web server during configuration.

---

### Post by BStrizzy on 2013-01-12
> **CharlesA said:**
> Purge phpmyadmin and reinstall it.

```
sudo apt-get purge phpmyadmin && sudo apt-get install phpmyadmin
```Be sure to select the correct web server during configuration.


got an error for some reason

---

### Post by tgalati4 on 2013-01-12
When you set up your LAMP server, did you change the default mysql port (3306)?  Is mysql even running?

```
ps -ef | grep mysql
```

---

### Post by BStrizzy on 2013-01-12
> **tgalati4 said:**
> When you set up your LAMP server, did you change the default mysql port (3306)?  Is mysql even running?

```
ps -ef | grep mysql
```

this is what I get when I enter that code: 

bstrizzy@nova:~$ ps -ef | grep mysql
mysql     2511     1  0 14:04 ?        00:00:07 /usr/sbin/mysqld
bstrizzy  4431  4428  0 18:23 pts/0    00:00:00 grep mysql
bstrizzy@nova:~$ 

I am not sure if my sql is running and not sure how to start it if that.

---

### Post by tgalati4 on 2013-01-12
To start any process:

```
cd /etc/init.d
ls -la
sudo apache start
sudo mysql start

```

Apache may automatically start mysql, so you will just get a message that mysql is already running.

If you are going to run web services, you will need to become familiar with all of the services listed in /etc/init.d.

Basic commands are start, stop, restart.

Your output shows that it ran for 7 seconds and then it probably quit.  Usually you get a few mysql entries with your username.  Look for mysql errors in /var/log/mysql.err or mysql.log.  The "d" in mysqld stands for daemon--a process that runs in the background and controls things, but remains hidden--sort of like--a demon.

---

### Post by BStrizzy on 2013-01-13
> **tgalati4 said:**
> To start any process:

```
cd /etc/init.d
ls -la
sudo apache start
sudo mysql start

```Apache may automatically start mysql, so you will just get a message that mysql is already running.

If you are going to run web services, you will need to become familiar with all of the services listed in /etc/init.d.

Basic commands are start, stop, restart.

Your output shows that it ran for 7 seconds and then it probably quit.  Usually you get a few mysql entries with your username.  Look for mysql errors in /var/log/mysql.err or mysql.log.  The "d" in mysqld stands for daemon--a process that runs in the background and controls things, but remains hidden--sort of like--a demon.

strizzy@nova:/etc/init.d$ sudo mysql start
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
bstrizzy@nova:/etc/init.d$ sudo apache start
sudo: apache: command not found
bstrizzy@nova:/etc/init.d$ sudo mysql start
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)
bstrizzy@nova:/etc/init.d$ cd /var/log/mysql.err
-bash: cd: /var/log/mysql.err: Not a directory
bstrizzy@nova:/etc/init.d$ 

I am just going to remove all the packages and start lamp stack over. i tried already but when i did i got an error message. if you scroll up a lil bit, you can see a screen shot of the error i get when im trying to delete it

---

### Post by steeldriver on 2013-01-13
those commands should be

```
sudo [COLOR=Red]service[/COLOR] mysql start
``` and so on I think

---

### Post by tgalati4 on 2013-01-13
And that should be apache2 not apache.  You need to look at the list of services available in /etc/init.d before you blindly try to start them!

It looks like mysql was not set up.  You need to go through a mysql configuration by creating a database with a proper administrator username and password.

man service

To learn more about starting services using the service command.  Either method works.

---

### Post by BStrizzy on 2013-01-16
Got it working you guys =). I just removed/purge everything dealing with LAMP. I even found out how to put wordpress on it!

---

