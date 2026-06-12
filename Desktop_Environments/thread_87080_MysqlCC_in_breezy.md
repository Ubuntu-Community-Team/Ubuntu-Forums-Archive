---
title: "MysqlCC in breezy"
date: 2005-11-07
forum: Desktop Environments
---

### Post by drekka on 2005-11-07
Hi there.

I've been using Hoary for a while now, but did a complete installation of breezy a  week ago.
I managed to run MysqlCC with Hoary, but with Breezy I can't get the application to work properly.

All text in MysqlCC are shown as squares. Odd signs.
What could be wrong? Why aint the normal text showed?

Thanks for any input...

---

### Post by KingBahamut on 2005-11-07
I believe in Breezy, under Add Applications there is a MySQL Administrator , is this the same utility your talking about?

---

### Post by drekka on 2005-11-07
[QUOTE=KingBahamut]I believe in Breezy, under Add Applications there is a MySQL Administrator , is this the same utility your talking about?[/QUOTE]
Jeah, you can execute queries with the Administrator as well, but I kinda like the CC better.
But anyway, I gave the administrator a shot and I get a error when supling the following:
host: localhost
user: root
pass: <empty>

The error I get:
connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'

I've installed the mysql-server packaged. Should that work then? I mean, the information is correct, aint that right?

---

### Post by KingBahamut on 2005-11-07
Ahhhhh, you havent set a mysql password yet. 

mysqladmin -u root -p to set password. 

Be aware that any apps / web dev youve done will be affected by this (an example would be the setting in a config.php file of a mambo/joomla install) and youll need to correct them.

---

### Post by Seth on 2005-11-07
MySQL Query Browser (mysql-query-browser) is a better choice. It obsoletes MySQL CC.

---

### Post by pestie on 2005-11-08
That's what the MySQL folks will tell you, but I can tell you from personal experience that it's a piece of crap compared to MySQLcc. I have two other developers here in our department who agree with me.

I'm tellin' ya, I'm getting pretty frustrated with useful tools being arbitrarily dropped from Ubuntu. First KCalc (like SpeedCrunch is supposed to be some sort of *replacement?!?*) and now MySQLcc. There are, what, tens of thousands of packages in the Ubuntu repositories? Why do we have to keep dropping useful tools? At least I could easily get KCalc back.

---

### Post by gbouro on 2005-11-08
There's a good pointer to a statically compiled mysqlcc in:

[http://ubuntuforums.org/showthread.php?p=477449](http://ubuntuforums.org/showthread.php?p=477449)

---

### Post by dmalopsy on 2005-11-20
I know the new query browser is very not that good, it is a very limited application. mysqlcc was alot better, it was a true mysql gui.
Im just gonna stick with hoary for the moment, until I find a way of getting mysqlcc myself.

[QUOTE=pestie]That's what the MySQL folks will tell you, but I can tell you from personal experience that it's a piece of crap compared to MySQLcc. I have two other developers here in our department who agree with me.

I'm tellin' ya, I'm getting pretty frustrated with useful tools being arbitrarily dropped from Ubuntu. First KCalc (like SpeedCrunch is supposed to be some sort of *replacement?!?*) and now MySQLcc. There are, what, tens of thousands of packages in the Ubuntu repositories? Why do we have to keep dropping useful tools? At least I could easily get KCalc back.[/QUOTE]

---

### Post by chantra on 2006-02-06
i made  a mysqlcc .deb for breezy.

you can get it from [http://debuntu.org]("http://debuntu.org")

Wish it helps :D

---

### Post by JELaVallee on 2006-02-16
[QUOTE=chantra]i made  a mysqlcc .deb for breezy.

you can get it from [http://debuntu.org]("http://debuntu.org")

Wish it helps :D[/QUOTE]

Thanks for this chantra!  It's a real life-saver not to have to mess with compiling this in the midst of a production crunch...

cheers,
Etienne

---

