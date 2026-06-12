---
title: "Error 2 when loading GRUB"
date: 2009-04-01
forum: General Help
---

### Post by jayjay960 on 2009-04-01
Ok, in my computer, I have 2 hard drives. One is 120gb and has XP. The other is 20gb and has Ubuntu. When I set Ubuntu up, it configured GRUB so that I could boot either XP or Ubuntu from it. Today I created a new 30gb partition on my 120gb hard drive, and installed Windows 7 Beta on it (Which I'm using now). When I tried to go back into XP however, I found that the only way to not load 7 was to change the boot sequence in my bios to load HDA-1 instead of HDA-0. Thing is, when I do this, it tells me grub is starting, then the line "Error 2" appears simply. Does anyone know how I could get this working? Also it'd be useful if I could also load WIndows 7 from GRUB, but I don't care too much if I can't.

---

### Post by WilliamJenningsBryan on 2009-04-01
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Tells you how to get Grub up and running again using a live cd.

A really good tutorial on editing the menu.lst file is here:

[http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/](http://boff.wordpress.com/2007/01/17/editing-bootgrubmenulst-to-change-the-grub-boot-menu/)

/boot/grub/menu.lst is the file Grub uses to create the boot menu.

To add Windows 7, just make an identical entry to Windows XP, but point it at the Win7 partition.

I hope this helps! Let me know if you have any more questions.

---

