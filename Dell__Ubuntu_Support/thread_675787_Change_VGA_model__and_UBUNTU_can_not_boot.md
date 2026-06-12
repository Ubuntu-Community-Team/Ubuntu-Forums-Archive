---
title: "Change VGA model  and UBUNTU can not boot"
date: 2008-01-23
forum: Dell  Ubuntu Support
---

### Post by usuntu on 2008-01-23
I have changed  VGA model in ubuntu screen menu into Intel 945GM (Dell Inspiron 6400) and after restrating the system it can not boot and gives an error :
***bcm43xx:Error : Microcode "bcm43xx_microcode5.fw" not available or load failed***
How can I reverse it and make it use its previous setting ? or how can I make it run in safe mode without booting with selected VGA ?
Dell Inspiron 6499
Ubuntu 7.10
VGA intel 945gm

---

### Post by Cresho on 2008-01-23
at log in prompt, choose failsafe and fix your problem there. It is under sessions before you log in, change to failsafe gnome.

---

### Post by usuntu on 2008-01-23
The error occurs before the login prompt. I do not have access into login prompt.

---

### Post by tekkenlord on 2008-01-23
When you turn on your computer, do you get a list of the available kernels, eg:

Ubuntu-2.26.22-4-generic
Ubuntu-2.22.22-4-generic (safe)
memtest+

If so, then press "e" on the first line and from the next dialog press the down arrow and "e" again. You will then be able to change the vga mode and boot normally to a graphic environment where you can change your vga mode once and for all.

---

