---
title: "no boot with kernel 2.6.38-13 and external display"
date: 2011-12-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jeff Murdoch on 2011-12-02
Dell Latitude E6410 - updated recently to Ubuntu 11/04 64 bit - not being connected to docking station neither external display (a fault?).

Since updating to kernel 2.6.38-13 some days ago no boot is possible when connected to docking station or external display via vga port. Machine is freezing. Successful start with previous kernel -12 . 

Any help appreciated. Maybe it would be better to switch to 11/10?


TIA

---

### Post by Miguel_ on 2011-12-13
Same thing is happening to me,  I just updated my system via update manager and now boot is not possible with the new kernel 2.6.38-13.      What's going on, I newer thought a simple system update was able to broke the system.   The only way I've found to fix this is by configuring default boot option at grub to automatically boot with previous kernel version 2.6.38-12; but why is the new kernel included in the official update channel if its not working with ubuntu 11.04 x64?, or am I making something wrong?.      Please ubuntu staff we need some help over here!.  Thanks in advance!.

---

### Post by wuffe on 2011-12-16
We have two systems here behaving the same way with the new kernel 2.6.38-13.

Both systems are Dell Latitude E6510 notebooks (no not E6410) both running Ubuntu 11.04 64bit. On both systems the previous kernel 2.6.38-12 works fine.

Note: It seems to be related to some Dell graphics option - no panics are produced - the system just freezes with a blinking (vga style underscore) cursor in the upper left corner.

---

