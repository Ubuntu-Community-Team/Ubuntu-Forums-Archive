---
title: "Can't read files off CD (privileges)"
date: 2006-09-16
forum: Desktop Environments
---

### Post by swaaye on 2006-09-16
I'm trying to use my Dreamweaver CD and install it with Wine. Problem is the CDROM's contents can only be viewed, not read or executed, unless I use sudo from the console. If I try to open say  .htm files off the disk it will tell me I don't have read privileges. As far as I can tell my user has CDROM access in the Users and Groups applet. 

This is a fresh install of Ubuntu 6.06

---

### Post by fistfullofroses on 2006-09-16
I have had the same problem. If you can use CDs in Ubuntu without Wine, then it is just a setting somewhere in Wine that you are going to have to search for... honestly that is the best way anyway considering that you will learn more. However, if CDs do not have privs in Ubuntu for users at all the problem would be in the /etc/fstab

---

### Post by swaaye on 2006-09-17
It appears to be an issue only with the Dreamweaver 8 CDROM. I tried two other disks, a CDR and a game CD, both of which are readable and the files openable.

Very odd.

---

