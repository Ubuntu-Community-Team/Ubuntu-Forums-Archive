---
title: "k10temp sensors modules source code??"
date: 2008-12-26
forum: Desktop Environments
---

### Post by hanbin973 on 2008-12-26
I can't find a proper source code. my kernel is 2.26.27-11

All the code that I got have problems in making .ko file.

Is there any way for this?

---

### Post by strange1712 on 2009-07-17
Hi, check this thread:
[http://ubuntuforums.org/showthread.php?t=1003916&page=2](http://ubuntuforums.org/showthread.php?t=1003916&page=2)
Specially comment #13.
Create a new dir, download the source:
[http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin](http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin)
rename it or save it as k10temp.c
Create the Makefile written in the page
[http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html)
(the first and general one), but change "k10temp.o" instead of "hello.o"
and then use sweetsinse's make instruction:

make -C /lib/modules/$(uname -r)/build M=$(pwd) modules

That should compile with a couple of warnings, then follow sweetsinse's steps.

Good Luck!

---

### Post by alexpage on 2010-01-05
This worked for me, thanks... but it only added the system temp (not CPU).

Hmm, a full year later... hopefully the support comes around.  I've also noticed that things like lshw and memtest don't detect memory settings correctly on my nForce 980a board... they all detect DDR3-1333 as 52GHz DDR2 at clocks 1-0-1 or some such nonsense.  (Not trying to start a new thread, just commenting on the general lack of hardware monitoring capability for the platform.)

---

