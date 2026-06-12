---
title: "PHP...HELP!!!! It wants to open instead of view, HELP!"
date: 2006-05-21
forum: Desktop Environments
---

### Post by romUdog on 2006-05-21
HEy guys i have ubuntu center installed and its a php thing...it was working so i could login but lately it has been really messed up as of a restart it wants to open the .php files instead of "reading" them and i dont know how to fix this as i think it is because maybe the php server isnt running but i dont know, can someone please help me?

---

### Post by adamkane on 2006-05-21
This is always a PITA to troubleshoot. Keep responding to your thread, until someone knowledgeable responds.

I hope you installed Apache/PHP4/MySQL4 this way:

```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
or Apache/PHP5/MySQSL4 this way:

```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

---

### Post by romUdog on 2006-05-21
i have everything installed correctly and apache and everything works and it did work until a recent reboot and now it wont view the php files it opens them as if downloading a file...

---

### Post by NoWhereMan on 2006-05-21
[QUOTE=romUdog]i have everything installed correctly and apache and everything works and it did work until a recent reboot and now it wont view the php files it opens them as if downloading a file...[/QUOTE]

try uninstall completely (removing also config files) and reinstall. looks like conf files/installation got messed up :) bye ;)

---

### Post by romUdog on 2006-05-21
NOOOOOOOOOOOOOOOOO i dont wanna it sucks it toooook sooooo long and then i gotta go re-make all those databases and users....oh well at least i didnt set them all up yet, lol!!! Kubuntu Drapper Rox!

---

### Post by romUdog on 2006-05-21
I went and reinstalled it ALL and it worked for all about 5 mins what do i do?

---

### Post by NoWhereMan on 2006-05-22
[QUOTE=romUdog]I went and reinstalled it ALL and it worked for all about 5 mins what do i do?[/QUOTE]

It's quite strange... are you on php5 or php4? I've no problems with php4 (ubuntu dapper), while another friend of mine has some problems with 5 (kubuntu breezy)...

unfortunately I can't help you more, i think

---

### Post by adamkane on 2006-05-22
!

---

### Post by Mau on 2006-05-23
Believe it or not, I found it much easier to install a LAMP5 server on Windows.  If you are just using a development machine, I recommend that you use: [www.apachefriends.org/en](www.apachefriends.org/en)

Also, as a PHP developer, please do not use PHP 4.  PHP 5 was released 2 years ago, with the beta even later.  It's very stable, and the sooner more people adapt it, the better it is for the rest of us.

---

### Post by adamkane on 2006-05-23
It is VERY easy to install a fresh LAMP on Ubuntu. See Post 2.

Apachefriends installs a huge list of apps, which is an even bigger pain to troubleshoot.

---

### Post by Mau on 2006-05-24
[QUOTE=adamkane]It is VERY easy to install a fresh LAMP on Ubuntu. See Post 2.[/QUOTE]

If you want to build it from the reps, then yes it's easier.  However, I would prefer to build it myself to get the latest versions (last time I checked PHP 5.0 was loaded, and not 5.1).

I'm not sure what you mean by the other huge list of apps though -- it's a development environment, so phpMyAdmin and other extensions do seem appropiate.  :)

---

### Post by adamkane on 2006-05-24
The apachefriends version installs many apps in addition to a basic LAMP setup.

Getting the latest apache/php/mysql (and phpmyadmin) to work together from source is a huge task, and is why we usually have to wait for someone to create some debs that have some assurance of working together as expected.

Keeping the latest LAMP up-to-date is also a huge error-prone task, and is not recommended either. 

(Do as you will though. I'm not trying to stop you.)

You're much better off with a dstribution that already has the latest LAMP available:
[http://distrowatch.com]("http://distrowatch.com")

---

### Post by cokehabit on 2006-05-26
i keep having exactly the same problem with Breezy :(

---

### Post by adamkane on 2006-05-27
See Post 2.

---

