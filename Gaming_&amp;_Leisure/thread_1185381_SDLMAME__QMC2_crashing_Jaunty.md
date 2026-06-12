---
title: "SDLMAME / QMC2 crashing Jaunty"
date: 2009-06-12
forum: Gaming &amp; Leisure
---

### Post by inverseroom on 2009-06-12
I succeeded in installing this emulator combination on my HP laptop (32-bit, AMD Tuion, 9.04) but when I load up a game and begin playing it, processor power starts getting sucked up, the fan gets faster and faster, and eventually the computer crashes so thoroughly I have to hold down the power button to switch off the machine.  Any ideas?  Thanks!

BTW, my version of Qt is 4.5.0.

---

### Post by disturbedite on 2009-06-12
well obviously check the logs.

also maybe try updating to Qt 4.5.1 and recompile QMC2 if you compiled it yourself.

---

### Post by inverseroom on 2009-06-14
Forgive me, but I'm not very experienced at any of this.  I installed everything using instuctions on the internet--I didn't know precisely what I was doing, and I don't know what I should check the logs for.  Can you give me a bit of guidance?  I considered updating Qt but can't figure out how to do it.  Is it a simple apt-get install command?  I tried apt-get install qt but the package obviously isn't called that.

---

### Post by disturbedite on 2009-06-14
check the logs located in ~/.qmc2 for errors.

to upgrade Qt, look for an ubuntu repo with the latest version of Qt (4.5.1 as of this writing).
(this is a far shot though as it seems like it is a problem with mame and not with the frontend, but i could be wrong).

---

