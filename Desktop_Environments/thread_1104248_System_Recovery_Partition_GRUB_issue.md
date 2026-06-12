---
title: "System Recovery Partition /GRUB issue"
date: 2009-03-23
forum: Desktop Environments
---

### Post by IfItMovesFunkIt on 2009-03-23
Just installed 8.04 as a dual boot with XP and I can no longer get access to the (XP) system recovery partition whilst system is booting up (F9 or F11 cant remeber which !!) as GRUB seems  to take control before I can press the approriate key.

Partition has not been nobled as far as I can see as can still see it in the "Hard Drive" section of the "Computer Management" tool of XP

Anyone got any ideas ??

---

### Post by jelle_ on 2009-03-23
you can add your recovery partition to grub, allowing you to boot in it. 

add the following lines to /boot/grub/menu.lst

title windows xp Recovery
root (hd0,0)
chainloader +1
savedefault

---

### Post by IfItMovesFunkIt on 2009-03-23
Appologies for being dumb ...... (this is my first ubuntu install)

so I should be able to Re-install XP using the linux supplied bootloader (GRUB) should the need arise !

T on Y

---

