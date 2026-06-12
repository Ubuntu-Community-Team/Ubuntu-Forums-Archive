---
title: "anybody have the candido-engine package?"
date: 2007-01-03
forum: Desktop Environments
---

### Post by sinisterguy on 2007-01-03
Hello everybody,

i just recently did a fresh install of ubuntu. Somehow some data got corrupted when i was backing it up (lost all my photos, some of my portfolio ones too, but thats another story ](*,) ). anyways, I lost the local copy of the candido-engine ubuntu package that I had. I've been trying to get to the candido website ([http://candido.berlios.de](http://candido.berlios.de)) for the entire morning but I can't get there. So i was wondering. Does anybody happen to have that package lying around somewhere?

-Lukas

---

### Post by pete83 on 2007-01-03
I second this request. The [http://candido.berlios.de](http://candido.berlios.de) website has been down for a couple weeks now, and I can't find the candido-engine package anywhere else.

Please help us, somebody!

---

### Post by sinisterguy on 2007-01-05
nevermind, the berlios site is back up :)

---

### Post by s04bf1c2 on 2007-01-11
Hi, site appears to be down again. I would be obliged if someone could post the package here.

**No worries, sites back up

---

### Post by sinisterguy on 2007-01-12
here's the deb. I posted it because of the inconsistency of the cnadido site. Don't forget to move the library files to the right spot if you're on edgy :)

---

### Post by revertex on 2007-01-24
anybody have an UPDATED the candido-engine package?

This one is compiled against gkt-2.4, i tried to compile manually, but it complains about missed gtk-2.8, but gtk-2.10 is installed.

any hints?

---

### Post by sinisterguy on 2007-01-24
a simple way around it is to just copy the files in /usr/lib/gtk-2.0/2.4.0/engines to the same directory in 2.10.0 one. As for the compilation error, do you have the gtk dev files installed?

---

### Post by revertex on 2007-01-25
@sinisterguy

Thank you, your tip has very valuable, copy didn't  work, but all that i need is install libgtk2.0-dev and all it's 30 dependencies.

I decide to compile because the old version didn't wokr anymore.

thanks to aptitude i can install all these dev packages just to compile candido, then remove everything without leave a trace of uneeded packages lying around, aptitude purge rules!

i created a candido deb package with checkinstall if someone like it i can share.

---

