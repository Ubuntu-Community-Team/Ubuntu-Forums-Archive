---
title: "Phpmyadmin"
date: 2009-05-29
forum: General Help
---

### Post by G9M29 on 2009-05-29
Hello. 
I've just installed PHPMYADMIN (after long day, no working ). Ok that's fine, but I wanna know how to log in. Tried username: root password: ANYTHING i can come with, but nothing is working. I looked for $cfg[Server][$i][password] and so.... but can't find it. So please help me log in in phpmyadmin, if it's need i will change the password and the username, but HOW? 

(I'm do not know nothing about Ubuntu ( Just installed ) - Desktop Edition 9.04 )

---

### Post by mbeach on 2009-05-29
You might just be lacking the root password for the mysql server (not the same as your linux user passwords). 

See
[https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20root%20password](https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20root%20password)

for details.

---

### Post by G9M29 on 2009-05-29
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

I think that the path to the dir is incorrect but no work ( I don't know how to change it :( )

---

### Post by mbeach on 2009-05-29
try:
```
sudo /etc/init.d/mysql start
``` and post the output.

This should start your mysql service. When do you get the 2002 error? When trying to connect with phpmyadmin or when using the steps at [https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20root%20password](https://help.ubuntu.com/community/ApacheMySQLPHP#Set%20mysql%20root%20password) ?

---

### Post by G9M29 on 2009-05-30
#2002 - &#1053;&#1103;&#1084;&#1072; &#1086;&#1090;&#1075;&#1086;&#1074;&#1086;&#1088; &#1086;&#1090; &#1089;&#1098;&#1088;&#1074;&#1098;&#1088;&#1072; (or the local MySQL server's socket is not correctly configured)

^ That's when I try to log in in PHP, 
in Terminal - the same error ](*,)[-o< help

---

