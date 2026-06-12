---
title: "Display Problem On Boot Up. PLEASE HELP!!!!"
date: 2009-01-07
forum: General Help
---

### Post by ramjedi on 2009-01-07
I recently installed updates for my Ubuntu 8.1 version. I remember one was for a video update. Now when I turn my Dell Inspiron 6000 on, There is text for about two seconds, and after the hard drive begins to boot up Ubuntu, the screen goes black. I have to restart over and over and eventually the display operates normally. I am not able to see long enough to get into the boot menu to try and fix the X server. I have got it working properly now so I will not try to restart until I get some advice. PLEASE HELP!!!!

Ramjedi

---

### Post by alan34 on 2009-01-07
In a terminal (Applications - Accessories - Terminal) type

sudo cp /boot/grub/menu.lst /boot/grub/menu.backup07012009

then type

gksudo gedit /boot/grub/menu.lst

scroll down to this line

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         **10**


and alter this time (in bold) to what you want. Your might be 3 as you see mine is 10.

-----------------------------------------------------------

to restore the original file

sudo cp /boot/grub/menu.backup07012009 /boot/grub/menu.lst

best of luck

---

