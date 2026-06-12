---
title: "[SOLVED] Can't add user in MySql"
date: 2008-12-06
forum: General Help
---

### Post by clay7 on 2008-12-06
I opened the terminal and typed this (with my real name and password):

*mysql> GRANT ALL PRIVILEGES ON *.* TO 'yourusername'@'localhost' IDENTIFIED BY 'yourpassword' WITH GRANT OPTION;*

and got this response:
[I]
ERROR 1045 (28000): Access denied for user ''@'localhost' (using password: NO)[/I]

So how do I add a user? I'm running 8.10 (installed less than a day), MySql 5 and Apache2.

Thanks!

---

### Post by eBoxNet on 2008-12-06
You need to login as root on mysql before you try to add a user.

check this : [http://dev.mysql.com/doc/refman/4.1/en/adding-users.html](http://dev.mysql.com/doc/refman/4.1/en/adding-users.html)

:)

---

### Post by clay7 on 2008-12-06
I tried that. Here's what I did:

From Terminal, I did this:
clay@clay-desktop:~$ mysql --user=root mysql --password=**** mysql

...and the terminal displayed a bunch of stuff beginning with this:

mysql  Ver 14.12 Distrib 5.0.67, for debian-linux-gnu (i486) using readline 5.2
Copyright (C) 2000-2008 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license
Usage: mysql [OPTIONS] [database]
.
.

then, in terminal, I logged in as root and typed this:
mysql

and got this:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

What now?

---

### Post by reality1011 on 2008-12-06
You should log in like this: 

mysql --user=root -p

you will be prompted for your password...

---

### Post by clay7 on 2008-12-06
it did prompt me for the password, but I got the same error message except that (using password: Yes)

i used both my password and root's password, but nothing worked. This setup is less than 24 hours old, so I know they're the right passwords.

what should I do?

---

### Post by clay7 on 2008-12-06
i saw on some other site that this is what i need to do from terminal:

/usr/bin/mysql -u root -p

THIS WORKED! 

This is what I was doing, but it did not work:

mysql -u root -p

---

### Post by reality1011 on 2008-12-06
thats odd... paste the output of the following:

which mysql

---

### Post by clay7 on 2008-12-06
which mysql 
produced
/usr/bin/mysql

Is something off with this?

---

### Post by reality1011 on 2008-12-06
thats odd... when you type "mysql -u root -p" by itself it doesnt work for you but typing "/usr/bin/mysql -u root -p " does....

log in as root then do mysql -p again ... that should prompt you for roots mysql password and should work....

If it does, great everything sounds good and we can chalk it up to misunderstanding due to writing description... otherwise it would be odd

---

### Post by clay7 on 2008-12-06
yeah, it works now. I'm just happy!

---

### Post by reality1011 on 2008-12-07
Great.

---

