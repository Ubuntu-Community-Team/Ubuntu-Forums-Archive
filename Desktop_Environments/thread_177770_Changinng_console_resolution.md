---
title: "Changinng console resolution"
date: 2006-05-16
forum: Desktop Environments
---

### Post by LordRaiden on 2006-05-16
How do I change the resolution when I am using Kubuntu in console mode? (logging out and logging in console mode)

Thanks in advance

---

### Post by vidak on 2006-05-17
try to enter boot parameter vga=*** at boot , where *** is a three-digit number.

Colours 640x400 | 640x480 | 800x600 | 1024x768 | 1152x864 | 1280x1024 | 1600x1200
--------+--------------------------------------------------------------
4 bits | ? | ? | 0x302 | ? | ? | ? | ?
8 bits | 0x300 | 0x301 | 0x303 | 0x305 | 0x161 | 0x307 | 0x31C
15 bits | ? | 0x310 | 0x313 | 0x316 | 0x162 | 0x319 | 0x31D
16 bits | ? | 0x311 | 0x314 | 0x317 | 0x163 | 0x31A | 0x31E
24 bits | ? | 0x312 | 0x315 | 0x318 | ? | 0x31B | 0x31F
32 bits | ? | ? | ? | ? | 0x164 | ?


Key: 8 bits = 256 colours, 15 bits = 32,768 colours, 16 bits = 65,536 colours, 24 bits = 16.8 million colours, 32 bits - same as 24 bits, but the extra 8 bits can be used for other things, and fits perfectly with a 32 bit PCI/VLB/EISA bus.


([http://www.linuxquestions.org/questions/showthread.php?p=2189665](http://www.linuxquestions.org/questions/showthread.php?p=2189665))

---

