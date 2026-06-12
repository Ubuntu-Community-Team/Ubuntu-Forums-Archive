---
title: "mySQL 4.1x"
date: 2006-01-03
forum: General Help
---

### Post by tbresson on 2006-01-03
Hi there.

I'm running Ubuntu 5.04 and like to run a mySQL server. Nothing major or anything, just for the fun of it really. Mostly it will be used as a testing scenario for my web development.

I tried to look around for some help but most of the things I found was pretty straight forward, but didn't work.

Could anyone be helpful setting me up?

After installation I sat the password for the root user with:
mysqladmin -u root password db_user_password 

Then I was told to edit my config file so I could connect to the database from someplace else than localhost.

sudo gedit /etc/mysql/my.cnf 

"skip-networking" was not to be found in the config file though, it seems it's an option for previous releases of mySQL.

#bind-address = 127.0.0.1 is even commented-out like it's supposed to.

And I have restarted the daemon, /etc/init.d/mysql restart 
after the changes in the config file was made.

But I still can't reach the server from a remote client (on the same LAN).

---

### Post by tbresson on 2006-01-05
I guess I'll just try and install the 4.0x version instead and remove comment-out the skip-networking people write so much about, and see if that works.

Otherwise I might take a look at myphpadmin which runs a webinterface which can then be controlled from any other PC.

---

### Post by tbresson on 2006-01-09
Well.. I tried to install version 4.0x instead. It didn't work!
I removed the skip-networking as described all over the Internet. 

Here's the deal:
I try and connect with MySQL Administrator 1.1.3 from a WinXP.

With #skip-networking set in the conf. file I get this error:

Could not connect to the specified instance.
MySQL Error Number 1130
Host '192.168.1.4' is not allowed to connect to this MySQL server

Maybe it's because I connect with user "root" ?

Please help !!

---

### Post by cotn on 2006-01-14
Did you try this:

```

$ mysql -u root -p

mysql> GRANT ALL PRIVILEGES ON db.*
    -> TO root@'192.168.1.0/255.255.255.0';

```

---

### Post by tbresson on 2006-01-14
Now it simply states:

Query OK, 0 rows affected (0.44 sec)

I found out if I conenct my MySQL Administrator I can access the database with user root, and if the password is blank.

This seems weird.

---

### Post by cotn on 2006-01-14
[QUOTE=tbresson]Now it simply states:

Query OK, 0 rows affected (0.44 sec)

I found out if I conenct my MySQL Administrator I can access the database with user root, and if the password is blank.

This seems weird.[/QUOTE]

So what you mean is that you can login mysql-server from a remote host with root and no password and you would like to set a password for root ?

---

### Post by tbresson on 2006-01-15
No.. not really.

I have a mySQL DB on my Ubuntu, and I would like to create and alter my db tables from my WinXP which is on LAN with the mySQL server.

I wasn't able to logon to the server from my WinXP machine, so I looked around for disabling the #skip-networking (mySQL 4.0x) or the #bind = 127.0.0.1 (mySQL 4.1x). After removing this I did get an error when connecting instead of just something about the server no listening. The error was that I wasn't able to connect to my database.

I tried some grant all privileges, but I still couldn't get it to work.

Suddenly I tried connecting to the server where I forgot the password (root on the server of course has a password) but I got in without one. This seems weird to me. Shouldn't a remote logon to the mySQL database have the same username and password as the one I entered after installation of the mySQL.

Where I did something like this:
mysql -u root -password <root_password_of_my_choice>

The password I chose here is the same as the password of the root user on Ubuntu (to make sure there's no confusion).

---

### Post by cotn on 2006-01-17
[QUOTE=tbresson]No.. not really.

Where I did something like this:
mysql -u root -password <root_password_of_my_choice>

The password I chose here is the same as the password of the root user on Ubuntu (to make sure there's no confusion).[/QUOTE]

Ok. it's possible and almost likely that you have two mysql root acccounts. One for localhost, and one for a host @192.168.x.x.

Can you give a dump of your user table of your mysql databese. 

by example: 

```

$ mysql -u root -p
> use mysql;
> select host, user  from user where User='root';

```

---

### Post by tbresson on 2006-01-24
I found two entries:
localhost
and
myserverhostname

Should I try something like this?
mysql -uroot -ppassword  "GRANT ALL PRIVILEGES ON *.* TO root@'192.168.1.0/255.255.255.0' identified by 'theRootPassword';"

Oh.. I forgot; someone told me to try and add my hostname in the /etc/hosts file when having a mysql server, e.g.

192.168.1.3 myhostname

---

### Post by cotn on 2006-01-24
> **tbresson]
Should I try something like this?
```

> GRANT ALL PRIVILEGES ON *.* TO root@'192.168.1.0/255.255.255.0' identified by 'theRootPassword' said:**
> 

I think this will do because you did already a 'GRANT ' command on the db:
```

SET PASSWORD FOR 'root'@'192.168.x.x' = PASSWORD('******'); 

```

More alternative methods here: [http://dev.mysql.com/doc/refman/4.1/en/default-privileges.html](http://dev.mysql.com/doc/refman/4.1/en/default-privileges.html)

> 
Oh.. I forgot; someone told me to try and add my hostname in the /etc/hosts file when having a mysql server, e.g.


But if this works:
[quote]
Suddenly I tried connecting to the server where I forgot the password (root on the server of course has a password) but I got in without one.


Then the problem has nothing to do with your /etc/hosts file.

---

