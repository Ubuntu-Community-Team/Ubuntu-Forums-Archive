---
title: "Dosbox front-end"
date: 2010-10-11
forum: Gaming &amp; Leisure
---

### Post by ELD on 2010-10-11
Okay everyone i am looking for a simple front-end to dosbox that works with an installed dosbox via software centre (so one that doesn't come with it's own install).

Can anyone recommend me one?

---

### Post by Shazzner on 2010-10-11
> **ELD said:**
> Okay everyone i am looking for a simple front-end to dosbox that works with an installed dosbox via software centre (so one that doesn't come with it's own install).

Can anyone recommend me one?

Back in my windows days I used D-Fend, not sure if there is a linux port or not.

Edit: did some quick research and people pointed to this:
[http://members.quicknet.nl/blankendaalr/dbgl/](http://members.quicknet.nl/blankendaalr/dbgl/)
DBGL - DosBox Game Launcher

---

### Post by ELD on 2010-10-11
See i used that but it comes with dosbox and i cannot get it to work with a .deb installed version.

Just seems annoying that if i uninstalled dosbox from software centre it removed the sdl libs the dosbox that comes with that launcher needs to work.

The main problem is i can't find the right sdl libs to install on their own to get the standalone version included in dbgl to work. Could anyone point me in the right direction who uses that launcher?

---

### Post by mastablasta on 2010-10-14
what seems to be the problem? it says:
Full support for DOSBox 0.74
 
if dosbox already comes with it just use that one...or you can always launch the programme by yourself from dosbox.
 
> sdl libs the dosbox that comes with that launcher needs to work.
 
Just install the libs from synaptic.

---

### Post by ELD on 2010-10-14
Well if you read this:

> 
The main problem is i can't find the right sdl libs to install on their  own to get the standalone version included in dbgl to work. Could anyone  point me in the right direction who uses that launcher?


You would see that is my problem.

---

### Post by Perfect Storm on 2010-10-14
```
sudo apt-get install libsdl-sound1.2 libsdl-net1.2 libsdl-image1.2
```

---

### Post by doorknob60 on 2010-10-14
My personal favorite is D-Box: [http://code.google.com/p/dbox/](http://code.google.com/p/dbox/)

---

### Post by xain72 on 2010-10-19
Try this

[http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/](http://home.quicknet.nl/qn/prive/blankendaalr/dbgl/)

DOSBox Game Lancher (Java based, open source)

D-Fend like GUI, very nice.

---

