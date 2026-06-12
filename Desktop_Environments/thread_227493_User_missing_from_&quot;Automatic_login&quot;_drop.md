---
title: "User missing from &quot;Automatic login&quot; dropdown"
date: 2006-08-01
forum: Desktop Environments
---

### Post by jeeves on 2006-08-01
For some reason the automatic login feature does not work for the second user account on my dapper install. When I go to **administration > login window > security tab > Automatic login user drop down menu** I can only see one of the two user accounts. 

Anyone know why this is happening? The missing user in question is a "mythtv" account, but I doubt that would have anything to do with it.

---

### Post by simonn on 2006-08-01
Just a guess, but IIRC automatic login uses the same rules as switching users, see my thread:

[http://ubuntuforums.org/showthread.php?t=205040](http://ubuntuforums.org/showthread.php?t=205040)

In /etc/X11/gdm/gdm.conf make sure mythtv's uid is > MinimalUID and that mythtv is included in the include line.

---

