---
title: "Black screen: How to use custom resolution"
date: 2009-01-06
forum: General Help
---

### Post by blazemore on 2009-01-06
This is a toughie. On a netbook with a non-standard native resolution (1024 x 600), after usplash, the screen goes blank.
It also goes black if I use startx from the command line. (startx)
Basically, X is running, but the screen isn't displaying it?
Is there a way I can get the damn thing to run on the screen, with the liveCD? I want to install Ubuntu on this (Actually Easy Peasy but base Ubuntu has this problem too).

---

### Post by tuxxy on 2009-01-06
Seems the resolution may be the cause if you recently changed it aswell, you could try a simple xfix by booting the machine and at the GRUB screen press Delete button on keyboard - at the menu that appears you will select the recovery mode option and at the next one select the xfix option once the process is complete select continue with normal boot.

---

### Post by blazemore on 2009-01-06
This is first boot, from the live cd. Could you please tell me how to:
1. Stop X from the command-line on another virtual terminal
2. Start X with a custom resolution

---

### Post by blazemore on 2009-01-06
K i stopped x with /etc/init.d/gdm stop

How can I make it display as 1024 x 600?

---

### Post by blazemore on 2009-01-06
[http://ubuntuforums.org/showthread.php?t=1011226](http://ubuntuforums.org/showthread.php?t=1011226)

I found this. I PMed Matt to send me his xorg

---

