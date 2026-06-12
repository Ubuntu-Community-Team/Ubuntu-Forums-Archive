---
title: "mythtv... without a mythtv user"
date: 2005-08-28
forum: Desktop Environments
---

### Post by Chareos on 2005-08-28
Hi all.


I've installed mythtv 0.17 from universe.

I noticed that during installation a new user "mythtv" have been created.
I can't access mythtv-setup or the frontend cause they have no access to database from my main user.

Now, I don't want to relog as that mythtv user: I use mythtv on a secondary monitor (tv) WHILE still using pc on main monitor.

How could I transfer / delete and recreate myth database for my main user, then safely delete that mythtv user ?


MANY thanks
Fabio

---

### Post by dk5151 on 2006-10-29
Anybody have an answer for this?

---

### Post by superm1 on 2006-10-30
The user account you launch mythfrontend as has no baring on the permissions to the database.  Either way, you just need to have the appropriate information to log into the database.  This information is stored in /etc/mythtv/mysql.txt

Copy that information into ~/.mythtv/mysql.txt for the user you want to launch the frontend as, and you will be able to run the frontend as that user.

---

### Post by dk5151 on 2006-10-30
Thanks, it's running smoothly now.

---

