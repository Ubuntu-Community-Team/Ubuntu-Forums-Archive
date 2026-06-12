---
title: "Screen off Center"
date: 2007-04-20
forum: Desktop Environments
---

### Post by jprez1980 on 2007-04-20
Hi Gang,

I'm new to the whole Ubuntu thing, just got version 7.04 up and going.  My question is, when the GUI appears it is off center on my monitor.  After logging in, it is still off center.  Beyond the control of the monitor settings.  I seem to remember a program in FreeBSD called xvidset but its not on here.  I have a ViewSonic LCD monitor and an older nVidia GeForce2 MX card.  Any suggestions here would be great.  Also, when looking at the xorg.conf file I notice the monitor is being detected as "Generic"

Thanks!

---

### Post by dcstar on 2007-04-22
> **jprez1980 said:**
> Hi Gang,

I'm new to the whole Ubuntu thing, just got version 7.04 up and going.  My question is, when the GUI appears it is off center on my monitor.  After logging in, it is still off center.  Beyond the control of the monitor settings.  I seem to remember a program in FreeBSD called xvidset but its not on here.  I have a ViewSonic LCD monitor and an older nVidia GeForce2 MX card.  Any suggestions here would be great.  Also, when looking at the xorg.conf file I notice the monitor is being detected as "Generic"

Thanks!

There are special nvidia-legacy drivers you can install, and then run the command to reset your xorg.conf file to use them.

Do a forum search and you should find numerous posts with detailed steps to help you out.

---

### Post by john.nicholls on 2007-04-22
The Linux program is xvidtune.

---

