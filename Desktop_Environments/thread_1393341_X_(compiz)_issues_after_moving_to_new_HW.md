---
title: "X (compiz) issues after moving to new HW"
date: 2010-01-29
forum: Desktop Environments
---

### Post by perw on 2010-01-29
Hi
I've just moved my Karmic installation (Compiz enabled) from a Fujitsu-Siemens Lifebook E8420 (NVIDIA GeForce 9300M graphics) to a Lifebook S6420 (Intel GMA 4500M HD graphics) using the method described here [http://cheungtamhe.nl/blog/index.php?/archives/9-Moving-Ubuntu-installation-to-new-hardware.html](http://cheungtamhe.nl/blog/index.php?/archives/9-Moving-Ubuntu-installation-to-new-hardware.html) . 

I soon discovered that X wouldn't start. Booted in rescue mode and modified xorg.conf setting Driver to "intel" in the Device section. Testing with startx verified that basic X now worked. Rebooted and logged on but discovered that compiz wasn't working. Any attempt to turn on extra visual effects just gave me a mirror image which just timed out and returned me to basic desktop.

Just to check I booted the 9.10 Desktop CD in test mode and turned on extra visual effects and that worked ok.

What settings could be wrong here ? I've tried to reinstall xserver-xorg-core and xserver-xorg-video-intel but that didn't help any.

---

### Post by overdrank on 2010-01-30
Moved to Desktop Environments

---

### Post by perw on 2010-01-30
Solved !  
Seems my libGL.so.1 was symlinked to the old Nvidia lib. Removing the Nvidia libraries and reinstalling the libgl1-mesa-glx package did the trick.  I also removed some libGLCore.so libraries which i couldn't find belonged to any package.

---

