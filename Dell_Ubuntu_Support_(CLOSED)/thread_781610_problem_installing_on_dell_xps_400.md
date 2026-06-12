---
title: "problem installing on dell xps 400"
date: 2008-05-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by doalittledanse on 2008-05-04
im relatively new to linux, im trying to install 8.04. when i boot to either the live cd or the alternate one, my keyboard doesnt work, so i cant choose different boot options.  once the timer on the language selection screen runs out it loads, but when it looks like its done loading, the screen goes blank and then i get nothing.

i read that you have to change from AHCI to SATA and i tried that but got the same thing.  any suggestions?

---

### Post by doalittledanse on 2008-05-12
bump. anyone?

---

### Post by tptbz on 2008-06-19
I have the same problem.  I'm booting with the ubuntu-8.04-alternate-i386.iso; the alternate desktop CD with the text-based installer.  The regular ubuntu-8.04-desktop-i386.iso boots normally.  But I want to use the alternate ISO. 

When booting the "regular" DVD (not the alternate) there is a countdown prior to it booting into the live desktop.  My keyboard is unresponsive during the countdown.  After the countdown the live cd boots to the desktop.  After which the keyboard works.

Unfortunately, with the alternate DVD there is no countdown.  

Some things I tried in the BIOS:
Change USB Controller from "ON" to "No Boot"
Turned "Fast Boot" to "OFF"
Turned Num Lock "OFF"
Turned off Keyboard reporting errors.

I also booted with the regular Ubuntu DVD (not the alternate) and then while the countdown was going on I swapped the regular DVD with the alternate DVD but that failed to boot the system.  After the countdown it simply said that there was a DVD error.

Other OSes that work on this system are:
Arch
Slackware
XP
Vista
2003 Server

---

### Post by ragnarsson21 on 2011-04-10
Hey I had a similar problem, when I tried to use the keyboard to go into bios on my computer it did nothing at all. I realized that since it was a usb keyboard the usb was not usable in bios. So I used the ps2 keyboard and it worked fine. Since you have to configure you computer to use usb in bios, but you cant get into bios with a usb keyboard to configure it. You need the ps2 to change it. hope this helps.

---

