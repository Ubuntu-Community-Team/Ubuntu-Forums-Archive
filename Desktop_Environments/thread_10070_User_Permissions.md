---
title: "User Permissions"
date: 2005-01-04
forum: Desktop Environments
---

### Post by cmilhaus on 2005-01-04
Version 4.10

I am a Linux "sorta-newbie", I have installed Ubuntu on a stand alone machine where I am the only user. So far, everything has been swell, except; this morning I went to format a floppy disk, and was told "I don't have sufficient permissions" to format or write to a floppy.
How do I get these permissions ( or from where)?

---

### Post by jbh on 2005-01-04
right click on 'Floppy Formatter' and change the Command to gksudo gfloppy

speaking of Gnome permissions, anybody know how it's possible to delete files etc. while in Samba/File Browser? ie: right-click something and run in root only? I don't have any user permissions.

---

### Post by cmilhaus on 2005-01-05
Thank you very much! This works perfectly!! :mrgreen:

---

### Post by trash on 2005-01-18
I tried gksudo gfloppy but everytime i get a new error telling me the app quit, when i hit close i am then prompted for my password, then i get the same app quit error with status 1

Failed to run gfloppy as user root:
 Child terminated with 1 status

---

