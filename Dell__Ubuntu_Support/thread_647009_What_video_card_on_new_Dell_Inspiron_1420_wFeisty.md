---
title: "What video card on new Dell Inspiron 1420 w/Feisty?"
date: 2007-12-21
forum: Dell  Ubuntu Support
---

### Post by devi on 2007-12-21
I'm new to Ubuntu and I'm having a hard time figuring out what video card I have. 

My laptop:

Dell Inspiron 1420
Ubuntu 7.04 (factory-installed)

Where do I go to find this out? It's got to be in the device manager, but I don't know what to look for.

Thanks!!

---

### Post by divague on 2007-12-21
in a terminal type
$ lspci
and look vga compatible controller

---

### Post by natehall on 2007-12-21
You might have to type "sudo" in front of "iswh" I remember sudo as "Super User Direct Order!" A super user or Root user has the highest level of permission on a Linux system. "ls" is the command for list so lshw can be remembered as "LiSt HarDware" Just don't capitalize it, linux is case sensative!

---

### Post by desheffer on 2007-12-21
If you have an Inspiron 1420N factory installed with Ubuntu, as you said, then your video card should be an **Intel GMA X3100**, The chipset in this card is the **Intel GM965**.

---

