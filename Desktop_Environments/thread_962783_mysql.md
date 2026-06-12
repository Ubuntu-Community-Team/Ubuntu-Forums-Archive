---
title: "mysql"
date: 2008-10-29
forum: Desktop Environments
---

### Post by rusty_jones on 2008-10-29
I setup php mysql server on hardy to run amarok. I've been able to create a database amarok but when i go to grant user privelege I get an error: 

 GRANT ALL ON amarok.* TO stan@localhost IDENTIFIED BY "amarok";
ERROR 1146 (42S02): Table 'mysql.user' doesn't exist.

Since i am a newbie to ubuntu and have searched this forum without any luck, can some one point me in the right direction?

Rusty

---

### Post by drelyn86 on 2008-10-29
[Mike's Ubuntu Blog: How to: set up MySQL Database in Amarok]("http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html")

This guide has never failed me. 

I'm assuming where you messed up is that stan@localhost part where it should be amarok@localhost

Edit: P.S. You will love Amarok once it's set up on mysql

---

### Post by rusty_jones on 2008-10-29
I changed the user to amarok but still the same message.

mysql> GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY "amarok";ERROR 1146 (42S02): Table 'mysql.user' doesn't exist
 
Rusty

---

### Post by drelyn86 on 2008-10-29
Have you followed the steps in that guide?

And I think that you should have single quotes surrounding amarok instead of double-quotes.

---

### Post by rusty_jones on 2008-10-29
I followed everything in the manual. Every database i create I get the same error message 
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'amarok';ERROR 1146 (42S02): Table 'mysql.user' doesn't exist

Rusty

---

### Post by drelyn86 on 2008-10-29
Try this...

```
sudo apt-get --purge remove mysql-server mysql-client
```
```
sudo apt-get install mysql-server mysql-client
```

And try again from the beginning

---

