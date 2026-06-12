---
title: "Help!!!!!  Pleaseeee!!!!"
date: 2007-07-05
forum: Desktop Environments
---

### Post by Magiczero on 2007-07-05
Hi

My laptop is a dell inspron 2500 with ubuntu 7.04    When my laptop boots it gets past the GRUB thing & then there is no splash & then there is a yellow-grayish screen but then if i hit fn F7 the ubuntu login screen comes up.  Can you tell why I need to hit FN F7 everytime it boots?

Thanks

---

### Post by Gagle on 2007-07-05
Well to start off, the ctrl-alt F7 key is used to switch to the graphical login session.  By default Ubuntu will botot on that virtual terminal (tty).  Ctrl-Alt F1-6 are other virtual terminals for a command line login this time.  Maybe there is a bit confusion going at this level and gdm doesn't know which on to choose.

Have you tried re-installing or re-configuring gdm (Gnome Display Manager) ?

Hope it helps,

Gagle

---

### Post by Magiczero on 2007-07-05
I tried those already they dont fix it

---

