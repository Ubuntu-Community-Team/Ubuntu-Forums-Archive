---
title: "installing kde on ubuntu"
date: 2007-10-30
forum: Desktop Environments
---

### Post by Irti on 2007-10-30
hey........... i wanted to install kde on ubuntu....but i dont have the net at my place right now............is there a .deb file available on any site for installing kde on ubuntu...

---

### Post by bingoUV on 2007-10-30
How are you even going to download the .deb if you do not have net. 

If you mean to go somewhere and bring back, I can only suggest downloading the whole kubuntu CD iso, burn it on a CD. Now you can add the CD as a repository in synaptic. So installing kubuntu-desktop from synaptic will work. 

The disadvantage is that kubuntu CD is about 700 MB, whereas you just need less than 300MB of download , because you got the common stuff in ubuntu.

---

### Post by Irti on 2007-10-31
ya tht was my  plan...to download it from the net at my college......bt chuck it i will just wait for the 1st of november...thts wen i gt the net at my place

---

### Post by schorem on 2007-10-31
No need to download kubuntu. Just try the following

```
sudo apt-get install kubuntu-desktop
```

it should install KDE. If not try the following site and add some repositories

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by jespdj on 2007-10-31
All Ubuntu packages (deb files) can be downloaded manually from: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Folk Theory on 2007-10-31
Q: do i need a separate partition for KDE or i can use it for the same partition i use GNOME? how would i switch between the two? finally, does the same apply for xfce too?

---

### Post by -grubby on 2007-10-31
> Q: do i need a separate partition for KDE or i can use it for the same partition i use GNOME? how would i switch between the two? finally, does the same apply for xfce too?
no you do not need separate partitions.  you switch between the two by logging out, selecting session, and hitting KDE. Yes, the same applies for XFCE

---

### Post by Folk Theory on 2007-10-31
thats great! thanks a lot!

---

