---
title: "Only command line startup no gui?"
date: 2006-07-22
forum: Desktop Environments
---

### Post by iMac on 2006-07-22
When I start my freshley installed linux system it only starts up to command line, is there a command i can issue that will start gui?
Thanks

---

### Post by theconley on 2006-07-22
Um, try xinit...

If this is an ubuntu install, that's really not normal.

~Conley

---

### Post by VirtuAlex on 2006-07-22
Technically the command is startx

---

### Post by Dr. Nick on 2006-07-22
Did you download the server or desktop iso?

If you have a gui installed then 

startx

should start it, or give you a reason it couldnt start.. However if you installed the server version you didnt install a gui.

In that case you need to run

sudo aptitude install ubuntu-desktop

---

### Post by mssever on 2006-07-22
If the above don't work, try ```
sudo telinit 5
```
This tells your computer to go to runlevel 5 (GUI). If that doesn't work, then something must not be installed right. Do ```
sudo aptitude install ubuntu-desktop
``` and hopefully that will fix it.

**EDIT:** Didn't see Dr. Nick's post...

---

### Post by 3rdalbum on 2006-07-22
Are you actually on an iMac, or is that just your name?

If you get an error message which says that X Org can't find any screens, then you need to do:

sudo dpkg-reconfigure xserver-xorg

and try different settings.

---

### Post by VirtuAlex on 2006-07-22
people just rushed to help... ;)

---

