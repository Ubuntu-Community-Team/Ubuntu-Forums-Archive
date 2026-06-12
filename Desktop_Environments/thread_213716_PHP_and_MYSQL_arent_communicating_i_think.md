---
title: "PHP and MYSQL arent communicating i think?"
date: 2006-07-11
forum: Desktop Environments
---

### Post by cconk01 on 2006-07-11
I have wordpress, phpbb and this other database running on my server, all of which have stoped working. I could really care less about the wordpress and phpbb databse. As for the other i have backed it up using myphpadmin (weird i think i can use phpmyadmin but not others). Im not sure where to start, but on the webpage when i click wordpress i recieve this information.
```
Your PHP installation appears to be missing the MySQL which is required for WordPress
```
I hope this is enough information to get started. Any help would be great at this point.

---

### Post by thegnark on 2006-07-11
are you sure you've got mysql installed? if not, go to synaptic and search for "mysql-server-5.0"

install it if it's not already

---

### Post by cconk01 on 2006-07-12
humm... i just did an apt-get install for it and it said i already have it and the most current version. How could i check to make sure mysql is running? Should phpmyadmin run even if mysql isnt running? I ask this because myphpadmin does/is running...

---

### Post by lamego on 2006-07-12
The error message is not very clear.
I am reading it in 2 ways:
1 - You are missing the php mysql module (please look for it and install on the package manager)
2 - You are expected to manualy install/configure a mysql user and database to be used by the application (this should be noted on the application install instructions).

---

### Post by indytim on 2006-07-12
do a phpinfo() to find out quickly what is and is not running.

IndyTim

---

### Post by cconk01 on 2006-07-12
im not sure if i did this right, but i enter: 
```
phpinfo()
```into the command line.
When i execute this it disconects me (i putty in).

---

