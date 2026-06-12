---
title: "MySQL Install/configuration problem"
date: 2006-10-01
forum: Desktop Environments
---

### Post by StormNet on 2006-10-01
I am trying to install MySQL so that i can use it with a few projects that i will be working on. I tried finding a HOWTO but i kept getting a lot of posts with questions on MySQL and not a HOWTO. So i started following the installation guide found at:

[https://help.ubuntu.com/ubuntu/serverguide/C/databases.html](https://help.ubuntu.com/ubuntu/serverguide/C/databases.html)

but when i got to the line:

> sudo mysqladmin -u root -h localhost password newrootsqlpassword
I get the following error:
> 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

I am just curious if the installation procedure changed or if i am doing something wrong, or forgot a step entirely (although i am following the install guide at the link provided) Any suggestions would be greatly appreciated.

---

### Post by sitedesign on 2006-10-01
just incase, try:
sudo mysqladmin -u root -p newrootsqlpassword -h localhost password newrootsqlpassword
this is in case you have already changed the root password to that without changing the command as you pasted it.

---

### Post by StormNet on 2006-10-01
ok, right before you posted your reply i tried:
> sudo mysql -u root -pnewrootsqlpassword
and i logged into mysql with no problems. 
> mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
+--------------------+
2 rows in set (0.00 sec)
So i guess the question would be, what are the commands trying to do? I mean i can see that it is setting the root password to *newrootsqlpassword* in the first line, and in the second line, it is setting the root localhost password.

What is the difference between the two? I was searching through the MySQL Documentation page but couldnt find anything that explains what it is doing, or how to do the rudamentary setup. So is that line really necessary? And what would be the concequences if i didnt use it?

When i tried the command you suggested i got the following:> sudo mysqladmin -u root -p newrootsqlpassword -h localhost password newrootsqlpassword
Enter password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'
when using the root password.> sudo mysqladmin -u root -p newrootsqlpassword -h localhost password newrootsqlpassword
Enter password:
mysqladmin: Unknown command: 'newrootsqlpassword'
when i used the *newrootsqlpassword*.

BTW Thanks Peter

---

### Post by sitedesign on 2006-10-03
the mysqladmin is used to administer the mysql server.
The -h localhost I think says to connect to the host localhost which is your local machine.
password tells it to change the password of the user.

Type mysqladmin --help or man mysqladmin for a better description

The first command in the instructions sets the password for the mysql root user for the machine name, then the second tells it to change the password for the localhost account.
To explain that, the root user is allowed to connect from the localmachine or from the locahost, I know they are in effect the same thing but it's just the convention I think.

---

### Post by Buffalo Soldier on 2006-11-23
Have you tried this?
```
sudo mysqladmin -u root -p**[color=red]newrootsqlpassword[/color]** -h localhost password newrootsqlpassword
```

There is NO space between -p <-> newrootsqlpassword

---

