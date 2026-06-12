---
title: "Sturmbahnfahrer, a new arcade racing game"
date: 2006-07-10
forum: Gaming &amp; Leisure
---

### Post by NESFreak on 2006-07-10
[http://www.sturmbahnfahrer.com/](http://www.sturmbahnfahrer.com/)
In this game, you need along an obstacle course. It looks nice. while the dependencies are higher than the ones ubuntu has, it workes for me.

---

### Post by Rurouni on 2006-07-12
It doesn't work for me... it says something about "bad parameters for hw".

By the way... when I doble click it, it says that its not possible to install it because it's missed a library called "libasound"... but if I do an "dpkg -i", it gets installed (with some dependence lacks, but installed) and when I execute it (from command line) it shows the previous message.

Any suggestion? Thanks

---

### Post by Rosenrot on 2006-07-12
i also get 'libasound2" which i know is an ALSA library but i went to synpatic but its already installed ; /

---

### Post by Rosenrot on 2006-07-12
her is the error i get when opening with package installer

Error: Dependancy is not satisfiable: libasound2

---

### Post by seagull theme on 2006-07-15
i'm having this error too.  has anyone figured it out yet?

---

### Post by Perfect Storm on 2006-07-15
Yes, just hack the debian package and remove the dependency. Works great.

---

### Post by viciouslime on 2006-07-15
I've just tried that, but archive manager won't let me add the modified control file back into the package because of the folder being called ".".

How do I do it?

---

### Post by Perfect Storm on 2006-07-15
Save the .deb at Desktop

```
cd Desktop
mkdir Sturmbahn
dpkg-deb --extract sturmbahnfahrer_1.0-1_i386.deb  Sturmbahn
dpkg-deb --control sturmbahnfahrer_1.0-1_i386.deb  Sturmbahn/DEBIAN
nano Sturmbahn/DEBIAN/control
dpkg --build Sturmbahn
sudo dpkg -i Sturmbahn.deb

```

---

### Post by Perfect Storm on 2006-07-15
Just make sure that the dependency are met (though ubuntu uses a lower versions it still needs the libs ;) )

---

