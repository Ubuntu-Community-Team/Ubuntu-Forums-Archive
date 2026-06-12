---
title: "time to clean up    how ?"
date: 2008-03-06
forum: Desktop Environments
---

### Post by tropcky on 2008-03-06
after a long time of runing ubuntu and trying to learn how to install tar.gz and tar.bz2 
and all that stuff ( and still dont know how ) any way i fell that ther is alot of files in my system alot or bad and unworking files  in windows we use  a program to clean up the registry  so in ubuntu what should i do ? i just wany to clean up my system 

any help ?

---

### Post by kpkeerthi on 2008-03-06
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by overdrank on 2008-03-06
> **tropcky said:**
> after a long time of runing ubuntu and trying to learn how to install tar.gz and tar.bz2 
and all that stuff ( and still dont know how ) any way i fell that ther is alot of files in my system alot or bad and unworking files  in windows we use  a program to clean up the registry  so in ubuntu what should i do ? i just wany to clean up my system 

any help ?

Hi and you can try the commands 
```
sudo apt-get autoclean
sudo apt-get autoremove
```

---

### Post by tropcky on 2008-03-06
thank u

---

### Post by Arthur Archnix on 2008-03-06
Yeah, autoclean and autoremove are handy. Also, there's no registry so nothing really to clean up. Welcome to Linux, eh?

Another nice one is locale-purge.
```
sudo apt-get install locale-purge
```You'll be asked to select your language, choose the ones you need, e.g., if you use US english and UK english, you'd want everything with EN_US and EN_GB. Then
```
sudo locale-purge
```Totally unnecessary, but a fun little tweak.

EDIT: Might be localepurge ... I don't have root access right now so I can't confirm.

---

### Post by NightwishFan on 2008-03-06
The registry... :mad:

I remember that thing. Always needed cleaning. Any program installed was free to change it... Don't forget about the siblings that download and install any random "game" they see on the internet. All of a sudden my 128mb ram Windows Xp slug is trying to open 12 ie windows.

:cry: I love you linux.

---

### Post by tropcky on 2008-03-06
lol thank u all and we love linux

---

