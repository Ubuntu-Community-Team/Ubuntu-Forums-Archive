---
title: "ET - Quake Wars  Dedicated Server Installation"
date: 2007-09-26
forum: Gaming &amp; Leisure
---

### Post by littlewild on 2007-09-26
Hi all, I am trying to run a dedicated ETQW server on a 64-bit ubuntu 7.04 server installation.

Unfortunately I think the ETQW file requires 32 bit emulation of some sort to execute (can't remember where I saw that though). At the moment whenever I run the file the following error message appears and I am unable to continue. 

"STUBBED: ftell is 32 bit!
 at /home/timo/Build/mojosetup/fileio.c:246"

Has anyone here successfully installed the ETQW server or does any one know where I can find more information on setting up one?

---

### Post by pay on 2007-09-26
You will need some 32bit libraries. For example (I don't know which exact ones you need)```
sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk linux32
```

---

### Post by littlewild on 2007-09-26
Thanks for the heads up, will try it again after installing the 32bit libraries. :)

---

