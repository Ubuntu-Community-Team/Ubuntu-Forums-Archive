---
title: "mythtv network access"
date: 2006-12-22
forum: Gaming &amp; Leisure
---

### Post by crazedgremlin on 2006-12-22
EDIT: sorry wrong section

[I]Hi!  I just installed mythtv on my computer which is in the basement.
I was wondering if anyone can tell me how to access my recordings
on my other computer which is upstairs.

btw - both computers are on ubuntu :KS 


Thanks in advance!
-dan
[/I]
=========

---

### Post by SyvanX on 2006-12-24
Assuming they're on the same network, the easiest way to do it would be to install the MythTV frontend on your upstairs computer.  You'll also have to make sure you have networking enabled in your mysql config so your frontend can connect.
[B][U]
on the BASEMENT machine:[/U][/B]

```
sudo nano /etc/mysql/my.cnf
```

Comment out the line by placing a # at the beginning: 
> bind-address     = 127.0.0.1

```
sudo /etc/init.d/mysql restart
```

(or uncomment the skip-networking line depending on your mysql version)

Make sure you have a user that can access the tables,

Log into mysql (if you don't have a mysql root user password, leave off the '-p' before mysql)
```
mysql -u root -p mysql
```

then run the following query:
```
select user,host,password from user;
```

You should have a line that looks like this:

> | user             | host      | password         |
| mythtv           | %         | xxxxxxxxxxxxxx |
The important part is that host = '**%**', that allows it to login from any host, you should have a router blocking external port requests, so wildcarding hosts should be restricted to your local network.  If you know the password for your "mythtv | % |  " user you're ready for the frontend.  Otherwise you should set up a user with access to only the mythconverg database.  I use phpmyadmin, but I won't go into that usage here.

you can then exit mysql.
```
exit
```
[U][B]
on the UPSTAIRS machine:[/B][/U]

```
sudo apt-get install mythtv-frontend
```

then run:

```
mythfrontend
```

It should ask you a few setup steps, just enter the IP address of your basement computer, the mythtv user and password, and the database which should be mythconverg.

You should then be good to watch your recordings on your upstairs machine just like on your downstairs machine.  You can install some of the other plugins as well

```
sudo apt-get install mythplugins
```

---

### Post by crazedgremlin on 2006-12-25
Thankyou so much!  I will try this as soon as I get home from Christmas Vacation :)

---

### Post by ErikTheRed on 2006-12-27
You could either try that or setup samba shares to share the folder with your videos/recordings in it.

---

### Post by crazedgremlin on 2006-12-27
> **ErikTheRed said:**
> You could either try that or setup samba shares to share the folder with your videos/recordings in it.

True, but if I get the mythtv frontend on my upstairs computer I'll also be able to schedule recordings - plus I get l33t cred :)

---

### Post by SyvanX on 2006-12-29
That l337 cred is worth it, besides, you don't have to figure out what tv show "1045_20061229100100.mpg" is.  And it handles bookmarks and deletions, it's almost the same a watching directly on the backend.

---

