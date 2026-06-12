---
title: "grub turns off graphic card"
date: 2012-07-30
forum: Desktop Environments
---

### Post by zaza1851983 on 2012-07-30
I just did a clean install of 12.04 on my PC. I'm using my home folder from 10.04. There's also a windows 7 partition on the same hard disk

After the splash screen of the Bios, the monitor is turned off for a couple of seconds, then its turned on again on the ubuntu login screen. i.e. it totally skips the grub menu where I can load windows 7 Using grub-update and grub script info I know for sure that windows is on the grub menu. This is not just a black screen, the graphic card stops sending output to the screen, and thus the screen keeps blinking for a couple of seconds.

I have Radeon HD 6850 and installed the graphic driver from the repository

If while using ubuntu I pressed ctrl+shift+F1, or F2-F6, I get a black screen and my monitor keeps blinking as if its not getting output from the graphics card

Any idea?

PC Graphic Card: ATI Radeon HD 6850 
4 GB ram Fresh install of Ubuntu 12.04 64bit

Regards

---

### Post by alan21276 on 2012-07-30
Have a look here....I had a similar issue with a new install, it's something to do with the way the new linux kernel starts the graphics driver earlier on in the boot sequence. 

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

