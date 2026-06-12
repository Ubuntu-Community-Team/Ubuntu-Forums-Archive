---
title: "mounting an XP drive"
date: 2005-06-30
forum: Desktop Environments
---

### Post by robfindlay on 2005-06-30
I've recently just switched my desktop over to ubuntu and I was wondering why i can no longer mount my remote XP drive.  This is the command that always used to work under Slackware.

mount -t smbfs -o username=slag,  //192.168.0.5/c /mnt/croot/ 

Any ideas why this doesn't work. 


PS, I am able to access it via the "places" menu. 


Rob

---

### Post by irusun on 2005-06-30
You really need to take a look at this guide... should have most of the answers for what your asking...
[http://ubuntuguide.org/](http://ubuntuguide.org/)

HTH.

---

### Post by bdamon on 2005-07-01
[QUOTE=robfindlay]I've recently just switched my desktop over to ubuntu and I was wondering why i can no longer mount my remote XP drive.  This is the command that always used to work under Slackware.

mount -t smbfs -o username=slag,  //192.168.0.5/c /mnt/croot/ 

Any ideas why this doesn't work. 


PS, I am able to access it via the "places" menu. 


Rob[/QUOTE]

Just a guess but do you have smbfs installed?

apt-get install smbfs -s 


Ben

---

### Post by FLeiXiuS on 2005-07-01
[QUOTE=robfindlay]I've recently just switched my desktop over to ubuntu and I was wondering why i can no longer mount my remote XP drive.  This is the command that always used to work under Slackware.

mount -t smbfs -o username=slag,  //192.168.0.5/c /mnt/croot/ 

Any ideas why this doesn't work. 


PS, I am able to access it via the "places" menu. 


Rob[/QUOTE]


Error messages would help :-)

---

