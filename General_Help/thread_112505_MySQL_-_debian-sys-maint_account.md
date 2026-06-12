---
title: "MySQL - debian-sys-maint account"
date: 2006-01-04
forum: General Help
---

### Post by eggroid on 2006-01-04
I zapped the debian-sys-maint account right out of MySql doing a restore from a different distro - what permissions do I need to give this account?

Can anybody with MySql try this:

```
SHOW GRANTS for 'debian-sys-maint'@'localhost';
```

Thank you!

---

### Post by eggroid on 2006-01-04
bump!

Can somebody with mysql server installed help me out here?

---

### Post by eggroid on 2006-01-05
SOLVED

I did it myself by booting up a Live CD.

```
mysql> show grants for 'debian-sys-maint'@'localhost';
+---------------------------------------------------------------------------------------------------------------------------+
| Grants for debian-sys-maint@localhost                                             |
+---------------------------------------------------------------------------------------------------------------------------+
| GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD '1c26de472d9b41cf' WITH GRANT OPTION |
+---------------------------------------------------------------------------------------------------------------------------+
```

The strikes me as a little to much access though... I set it to:

```
GRANT RELOAD, SHUTDOWN, PROCESS, SHOW DATABASES, SUPER, LOCK TABLES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD '1c26de472d9b41cf'
```

At first glance this seems like enough to rotate the logs out.  But the default, for anybody else having the same problem, is all privileges on *.*, as above.

---

### Post by mediajunkie on 2006-10-28
Hi,

I have the same thing (loaded a dump from other server) and now I get :/etc/init.d$ /usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

I've tried:

GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD '1c26de472d9b41cf' WITH GRANT OPTION

but with no result. I still get the same error on restarting.
Is there any way to recover out of this? 

thanks

---

### Post by Kochin on 2006-10-29
Find your debian-sys-maint password in /etc/mysql/debian.cnf.

Then use
```
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;
```
Replace <password> with your debian-sys-maint password.

---

### Post by Abhi Kalyan on 2006-11-04
Am a new person here and am learling posting here as this thread interests my current Project.
Thank you

---

### Post by satimis on 2006-11-25
Hi folks,

Ubuntu-6.06.1-LAMP-server-amd64
MySQL - Ver 14.12 Distrib 5.0.22, for pc-linux-gnu (x86_64) using readline 5.1


I have the same problem on restarting MySQL

$ sudo /etc/init.d/mysql restart
Password:```

Stopping MySQL database server: mysqld...failed.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Killing MySQL database server by signal: mysqld.
Starting MySQL database server: mysqld.
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
satimis@ubuntu:~$ /usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

(the cursor hanging here.  I suppose waiting for input)

```

mysql> show grants for 'debian-sys-maint'@'localhost';```

ERROR 1141 (42000): There is no such grant defined for user 'debian-sys-maint' on host 'localhost'
```

/etc/mysql/debian.cnf is an empty file.

Please advise what shall I do?  How to fix it?  TIA


B.R.
satimis

---

### Post by hogman23 on 2007-01-03
> **satimis said:**
> 
mysql> show grants for 'debian-sys-maint'@'localhost';```

ERROR 1141 (42000): There is no such grant defined for user 'debian-sys-maint' on host 'localhost'
```

/etc/mysql/debian.cnf is an empty file.

Please advise what shall I do?  How to fix it?  TIA


B.R.
satimis

I would add something like this in the file:


# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = tdsclIL73xUw2ip2
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
user     = debian-sys-maint
password = tdsclIL73xUw2ip2
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr

---

### Post by satimis on 2007-01-05
Hi hogman23,

Tks for your advice.

I haven't touched mysql sometimes.  Strangely I found;

$ cat /etc/mysql/debian.cnf```

# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = qsN2OSgfrhI6AFzG
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = qsN2OSgfrhI6AFzG
socket   = /var/run/mysqld/mysqld.sock

```
It is now not an empty file.

What are those "password = qsN2OSgfrhI6AFzG"?  Tks.

B.R.
satimis

---

### Post by matsti on 2007-02-13
I had the same problem after an upgrade (I use Debian and apt). A new password was generated in /etc/mysql/debian.cnf but my existing mysql DB kept the password configuration as before the upgrade. Overwriting the password (qsN2OSgfrhI6AFzG in previous post) with my mysql password from before the upgrade did the trick. Hope this helps. M

---

### Post by stuporglue on 2007-02-19
I transplanted a mysql install from an older Ubuntu box, and got the same error. I did still have access as the mysql root user. I didn't have easy access to the old debian.cnf file. My solution was to change the password for the debian-sys-maint mysql user (I did it in phpmyadmin) and to put the new password (in plaintext) in the /etc/mysql/debian.cnf file. 

After that, a /etc/init.d/mysql restart brought everything back to normal. 

thanks for the pointers everyone :-)

---

### Post by squix on 2007-04-16
>stuporglue, matsti:

i can confirm that it works for me the same way as you did it.
thanks!

---

### Post by oljoha on 2007-04-24
> **Kochin said:**
> Find your debian-sys-maint password in /etc/mysql/debian.cnf.

Then use
```
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY '<password>' WITH GRANT OPTION;
```
Replace <password> with your debian-sys-maint password.

Worked for me. Thanx!

---

### Post by b_friedman on 2007-07-21
I had a similar problem with Ubuntu server 7.04, after doing a kernel upgrade.  Because this machine is on a closed intranet, I did a quick n dirty fix as follows:
1.  erase the password entries in /etc/mysql/debian.cnf for user debian-sys-maint
2.  log into mysql, using the mysql database, and reset the password for the user:
    grant all privileges on *.* to 'debian-sys-maint'@'localhost' identified by '' with grant option;
    flush privileges;

Note that this will create an insecure maintenance user, and shouldn't be used on any machine that can be accessed from the Internet.  After making these changes, you should not get errors related to the debian-sys-maint user (such as getting an error when trying:  sudo /etc/init.d/mysql restart)

Brent Friedman

---

### Post by Russian Mafia on 2007-10-24
> **mediajunkie said:**
> Hi,

I have the same thing (loaded a dump from other server) and now I get :/etc/init.d$ /usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

I've tried:

GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD '1c26de472d9b41cf' WITH GRANT OPTION

but with no result. I still get the same error on restarting.
Is there any way to recover out of this? 

thanks

Try use not  ```
...IDENTIFIED BY PASSWORD '1c26de472d9b41cf'...
``` but ```
...IDENTIFIED BY '1c26de472d9b41cf'...
```

---

### Post by edam on 2007-10-25
Thanks Russian Mafia, that works for me!

The correct incantation (for me at least) in mysql, is:
```
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY 'xxxxxxxxxx' WITH GRANT OPTION
```

---

### Post by sdhoigt on 2007-11-13
Me too, Russian Mafia.  

That must have changed or something because I had this same problem probably 6-9 months ago and I had 'IDENTIFIED BY PASSWORD' in my notes as the correct syntax.

Anyway, removing PASSWORD did the trick.

Thanks!
SD

---

### Post by whit on 2008-06-15
Just a note: When setting up MySQL replication according to standard methods in the MySQL docs, you'll also end up with this error on the slave. The solution is to copy the debian.cnf from master to slave, to have the password in sync.

IMHO, Debian innovations like this are usually a bad idea, since they introduce fragilities like this.

---

### Post by Backharlow on 2008-06-26
Another success by using the password (hash) from debian.cnf with the line:

GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD '' WITH GRANT OPTION

I had this problem because I stopped using the pre-release source for Hardy and just use the normal recommended updates, but doing this sort of orphaned a bunch of packages including mysql.

This thread was more helpful than over at Launchpad. Thanks everyone.:)

---

### Post by Backharlow on 2008-06-26
here is the Bug:
 [https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/153868]("https://bugs.launchpad.net/ubuntu/+source/mysql-dfsg-5.0/+bug/153868")

---

### Post by satimis on 2008-06-26
Hi folks,


It tooks me hours of work to fix the problem.  Finally I discover debian-sys-maint user being root user on Ubuntu 7.04.  


Ubuntu 6.06 also suffers the same problem.  I have to reinstall MySQL.  However I can create root user on this version.  


It is not a good idea to make change on the official package.  Debian did it.


About one week ago I also suffered on Cyrus taking me hours of work to fix the problem.  Debian made change on the official package.


satimis

---

