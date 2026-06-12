---
title: "MySql help with netjuke package"
date: 2009-04-06
forum: General Help
---

### Post by shortridge11 on 2009-04-06
I seem to not have something in mysql configured properly.  I installed the package netjuke
[http://sourceforge.net/projects/netjuke](http://sourceforge.net/projects/netjuke)
and I am having problems installing it.  I have the newest versions of apache2, php, and mysql.  The installation is done through a php page.  It asks for some basic info and requires you to create a user with access to a database, then makes some tables.  Somehow, when i make the user and the database, something isn't done right, and the installer only creates half the tables and then throws a generic error.  Here is a screenshot of the error.
[http://img16.imageshack.us/img16/6458/phpsql.png](http://img16.imageshack.us/img16/6458/phpsql.png)
If anyone has any idea how to figure out what's going on, please let me know.

for clarification, the sql user for netjuke is created with access to the database i'm using.  In fact, it creates half the tables before it throws that error.

---

### Post by cariboo on 2009-04-06
Have you tried changing the user to the one that was created when you installed mysql? Usually the user is root and the paswword is the one you created on install.

Jim

---

### Post by shortridge11 on 2009-04-06
well, i feel like setting the netjuke mysql user to root is pretty unsecure.  Is there anything else i could do?  I tried creating and deleting tables with the user i created and that worked no problem.  I'm avoiding using the root at all in this, other then creating the user with access to the netjuke table

---

### Post by shortridge11 on 2009-04-08
alright, just for testing purposes, i tried using root.  I got the same error =\. The problem isn't a permissions problem (or so it seems to me).  Maybe there is some kind of module i haven't enabled? i have no idea.  The screenshot is the only error i have, the mysql logs don't really help, because they are mysteriously blank.

---

### Post by shortridge11 on 2009-04-08
is there a mysql file i have to edit to give access? I'm trying to install this remotely, and i'm connected to the box setting up the databases via ssh.

---

### Post by shortridge11 on 2009-04-08
ok i semi-figured it out.  I was connecting using the http:xxx.net instead of localhost.  I changed it to localhost and now i get a little window popping up with the error
```

Problem executing part of the generated sql.
Please try again.
%0Acreate%20table%20netjuke_plists%20%28...

```

coming up.  I did a privilege check, and i have all the correct privileges on the table.  I'll check the logs and get back here when i figure something out.  If anyone is having the same problem please say something.  I feel like nobody else is having trouble installing this program and setting it up.

---

### Post by shortridge11 on 2009-04-15
anyone there?...

---

### Post by shortridge11 on 2009-04-22
I'm still getting errors when i try to do this, and i have no idea what to try anymore

---

### Post by crazyillspill on 2010-07-29
I'm having the exact same issue. Did you ever find a solution to this?

---

