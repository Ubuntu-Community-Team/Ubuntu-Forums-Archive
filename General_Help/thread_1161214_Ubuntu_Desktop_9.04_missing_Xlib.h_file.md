---
title: "Ubuntu Desktop 9.04 missing Xlib.h file"
date: 2009-05-16
forum: General Help
---

### Post by _dino_ on 2009-05-16
Hi Guys,
I am running Ubunto Desktop 9.04 and I am unable to locate my Xlib.h file which is supposed to be under usr/X11R6 directory.
I tried looking under other directories as well and searching for it using locate or find command but withotu success.
Anyone knows how to add X11R6 to my system so I can compile my programs.
Much appreciated
_dino_

---

### Post by michy99 on 2009-05-16
If you have installed libx11-dev, you will find Xlib.h in /usr/include/X11/ If not there, you probably need to 
```
sudo apt-get install libx11-dev
```

---

### Post by _dino_ on 2009-05-16
I did 
sudo apt-get install libx11-dev
 
but can not find it.  Where did it get installed?
 
Sorry, I am new to Linux
 
Thaks

---

### Post by _dino_ on 2009-05-16
> **michy99 said:**
> If you have installed libx11-dev, you will find Xlib.h in /usr/include/X11/ If not there, you probably need to 
```
sudo apt-get install libx11-dev
```
 
thanks, that helps :)
 
Much appreciated,
_dino_

---

