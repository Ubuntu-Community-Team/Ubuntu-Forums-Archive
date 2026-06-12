---
title: "IPOD Shuffle Rebulider for Windows"
date: 2007-04-24
forum: Desktop Environments
---

### Post by xflatlinex on 2007-04-24
I have the IPOD shuffle rebuilder for windows and have attempted to use it on Ubuntu64 7.04 with no luck. Normally in windows i just move an .exe file to my ipod, copy over the songs, then run the quick exe file and it will reprogram the ipod.  This prevents me from using Itunes.  I have tried to use this with WINE and it rebuilds but the results do not output to the IPOD.  anyone have any suggestions, or has anyone here had any success?
The program is at shuffle-db.sourceforge.net
thanks in advance

---

### Post by risidoro on 2007-04-26
Why don't you simply use the linux version of the program??? It is written in python so it should work both in linux (out of the box) and in windows (you have to install python first). BTW, the programmer strongly advise against using the C windows version (the .exe file) because it is outdated.

Bye

---

### Post by xflatlinex on 2007-04-26
Residoro,
I tried using the Python version but it will not run.  How do I install Python? I went to the Synaptic Manager and it shows its installed already?

---

### Post by miscz on 2007-04-26
Every time my Shuffle broke I just reformatted it (mkfs.vfat -f 32 /dev/sd-something, where your iPod is) and then installed correct stuff (db, etc) via Amarok.

---

### Post by airtonix on 2007-04-27
yeah gtkpod will take of your ipod. rebuilds it too. ;)

---

