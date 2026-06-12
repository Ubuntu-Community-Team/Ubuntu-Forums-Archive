---
title: "Question with mysql-server?"
date: 2009-05-19
forum: General Help
---

### Post by colau on 2009-05-19
Hi,
I installed mysql-server.
```

aptitude install mysql-server

```
Would anyone please tell how to start mysql-server and how to create account and set password?

---

### Post by prem1er on 2009-05-19
This is the cheat sheet I use for all of my MySql questions.  Did you think about installing phpMyAdmin yet?

[http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)

By default MySQL has no password for root access, so I suggest you set it with this.

```
mysqladmin -u root password NEWPASSWORD
```

Then you can login with.

```
mysql -u root -p PASSWORD
```

---

### Post by Cheesemill on 2009-05-19
The install should have prompted you to pick a root password.

MySQL should automatically start on boot, you can check if it's running by doing
```
ps ax | grep mysql
```

Cheesemill.

---

### Post by ActiveFrost on 2009-05-19
MySQL without a web server ( Apache/PHP ) ?
Add/Remove -> All and search for MySQL ( MySQL Administrator ).

---

### Post by kimda on 2009-05-19
starting:
sudo /etc/init.d/mysql start 

adding users:

read this document
[http://dev.mysql.com/doc/refman/5.1/en/adding-users.html](http://dev.mysql.com/doc/refman/5.1/en/adding-users.html)

an easier way to manage databases and users is to install phpmyadmin. then you can manage it from a webinterface.

---

### Post by colau on 2009-05-19
> **prem1er said:**
> This is the cheat sheet I use for all of my MySql questions.  Did you think about installing phpMyAdmin yet?

[http://www.pantz.org/software/mysql/mysqlcommands.html](http://www.pantz.org/software/mysql/mysqlcommands.html)

By default MySQL has no password for root access, so I suggest you set it with this.

```
mysqladmin -u root password NEWPASSWORD
```

Then you can login with.

```
mysql -u root -p PASSWORD
```
Thanks for your reply.
But if I use this "mysql -u root -p PASSWORD" and press ENTER it prompts me to enter password.
If I type the mysql-root password it says "ERROR 1049 (42000): Unknown database 'thepasswordientered'"

But if i type "mysql -u root -p" and press enter then it is all right.

---

### Post by prem1er on 2009-05-19
> **colau said:**
> Thanks for your reply.
But if I use this "mysql -u root -p PASSWORD" and press ENTER it prompts me to enter password.
If I type the mysql-root password it says "ERROR 1049 (42000): Unknown database 'thepasswordientered'"

But if i type "mysql -u root -p" and press enter then it is all right.

You didn't read my post correctly.  If you want to change your default root password, then run the command with 'mysqladmin'.  If you want to leave it as the default (which is nothing), then you can just login with "mysql -u root -p".

Wait are you saying that you have already changed the password and now it won't let you log in with that password?

---

### Post by colau on 2009-05-19
> **prem1er said:**
> You didn't read my post correctly.  If you want to change your default root password, then run the command with 'mysqladmin'.  If you want to leave it as the default (which is nothing), then you can just login with "mysql -u root -p".

Wait are you saying that you have already changed the password and now it won't let you log in with that password?
I read your post correctly.
I forgot to mention that I set a password for mysql-root account since it prompted to set a password for mysql-root account during installation.

---

### Post by prem1er on 2009-05-19
Ok, then try this.  And see if it will let you change your password.  

```
mysqladmin -u root password newpassword
```

See if it allows you to change it.  Then try to log in with the new password.

---

### Post by colau on 2009-05-19
> **prem1er said:**
> Ok, then try this.  And see if it will let you change your password.  

```
mysqladmin -u root password newpassword
```

See if it allows you to change it.  Then try to log in with the new password.
After this "mysqladmin -u root password newpassword"
```

mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

```

---

### Post by prem1er on 2009-05-19
If you already have a password set then you need to run this.  I think you mentioned this before.  This will salve your problem I believe.

```
mysqladmin -u LOGIN -p OLDPASSWORD NEWPASSWORD
```

---

### Post by colau on 2009-05-19
> **prem1er said:**
> If you already have a password set then you need to run this.  I think you mentioned this before.  This will salve your problem I believe.

```
mysqladmin -u LOGIN -p OLDPASSWORD NEWPASSWORD
```
Still problem.
```

mysqladmin: Unknown command: 'oldpassword'

```

---

