---
title: "accessing files"
date: 2009-05-01
forum: General Help
---

### Post by zacattack145 on 2009-05-01
I recently messed up my installation of ubuntu with a ATI driver. On this computer I have files that I need. So I put a live cd in, mounted the hard drive, found the file but couldn't access it because of my passwords.
Any ideas on how to access it?

---

### Post by slimx3m on 2009-05-01
in the terminal using the live cd just type
```
su -
```and then type the live cd password. with a super user you will be able to change the user permissions using
```
chmod ###
``` where ### is the permission e.g. 755

---

### Post by zacattack145 on 2009-05-01
thanks, hopefully it will work.

---

