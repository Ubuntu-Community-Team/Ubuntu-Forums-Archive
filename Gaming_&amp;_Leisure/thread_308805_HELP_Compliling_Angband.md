---
title: "HELP: Compliling Angband"
date: 2006-11-28
forum: Gaming &amp; Leisure
---

### Post by ghstzr0 on 2006-11-28
HELP!!

I am trying to get the old rougelike game Angband to compile under Ubuntu Edgy Eft.  I have download the 3.0.6 source from the Angband page and followed the directions carefully (which are few):

untar the source...
cd to source folder
run ./configure
run make and the make install

Every time I do this, the compilation seems to work, although the make verbose prints out a bunch of lines saying ¨nothing to do for target ...¨.  However, a binary IS created and so I try to run the game but I get this message:
./angband: Unable to prepare any 'display module'!

I have tried this on two computers (both using Edgy Eft).  Does anyone know why this would be happening??  Pleas help, I really need this for a school project!

---

### Post by zgornel on 2006-11-30
You are running the executable from the source directory ? If you are, after *make* do *make install*. It may be searching for some files in specific locations.

---

### Post by pKp on 2007-06-17
I had the same problem and couldn't resolve it. A simple way to avoid it is to install angband using apt-get - a package is present in the universe repository. 
Have fun playing Angband.

---

### Post by Celegorm on 2007-07-01
I know this is an old thread... but I had the same problem (under fiesty with angband 3.0.6) and eventually found a way to fix it. The actual problem had to do with some missing libraries. ```
sudo apt-get install libncurses5-dev libx11-dev
```
This should install the needed libraries, then try compiling again and it should run.

---

