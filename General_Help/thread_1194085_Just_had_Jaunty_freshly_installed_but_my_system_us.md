---
title: "Just had Jaunty freshly installed but my system usage is through the roof"
date: 2009-06-22
forum: General Help
---

### Post by ShamrockGold on 2009-06-22
I had someone very knowledgable do it for me but when I noticed that my music was skipping every two seconds I checked the monitor to find that I was pushing 100% with no processes running to explain it, except the very first time I checked in which nautilus was using a fair amount of juice.

Here are some of my system specs if it helps: Radeon 9800 Pro video card, AMD Athlon Processor (sorry I forget any further detail at this point and am not near my computer), 512 RAM, 80 gig HDD. 

I have ample room on my hard drive and everything seems to work fine, my computer usage just won't come down though even when nothing seems to be running. Let me know of any more information I can retrieve to help fix this problem. Thanks!

---

### Post by lovinglinux on 2009-06-22
I bet is the Remote Desktop server. Go to "System >> Preferences >> Startup Applications", disable the Remote Desktop and reboot.

You could also check if you have the proper hardware drive for your graphics card. Go to "System >> Administration >> Hardware Drives" and enable the proper drive.

If that doesn't solve, try [these tweaks](http://ubuntuforums.org/showthread.php?t=1152095).

---

