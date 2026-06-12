---
title: "Graphics Accelerator 3100 Intel in my Vostro 200"
date: 2007-09-03
forum: Dell  Ubuntu Support
---

### Post by Reise on 2007-09-03
What can I do? I need that ubuntu find the Graphics Accelerator 3100 Intel. What packages I need to download to  solve the problem?

Thanks.

---

### Post by rustalot on 2007-09-05
I think the package you want is 'xserver-xorg-video-intel'. After you install, do sudo dpkg-reconfigure -phigh xserver-xorg .Choose the 'intel' driver, and your resolution. Then reboot. If it doesn't work at first, try a lower resolution.

---

### Post by rnz0 on 2007-09-10
Hi, xserver-xorg-video-intel didn't work for me. X didn't start. Stuck with VESA at poor 1280x1024 resolution on a 22' LCD Viewsonic vx2235vm.

French people have the same problems here (but I can't read/understand french throughly):
[http://forum.ubuntu-fr.org/viewtopic.php?id=139491](http://forum.ubuntu-fr.org/viewtopic.php?id=139491)
Someone says:
"Le chipset G33 (et dérivés) n'existe pas encore pour notre distribution"  
So I guess support for this chipset is not ready on production yet.

Any light shed would be appreciated. :confused:

---

### Post by rnz0 on 2007-09-10
Hey guys, solved my problem. I add this driver xserver-xorg-video-intel_2.1.0-1ubuntu1_i386.deb here:

[http://ubuntuforums.org/showthread.php?t=494943](http://ubuntuforums.org/showthread.php?t=494943)
KEYWORDS
Intel intel-video xserver-xorg-video-intel xf86-video-intel 965 965GM i965 i965GM X3100 Santa Rosa SantaRosa CentrinoDuo Centrino Duo Dell Latitude D630

Then reconfigured X11 with sudo dpkg-reconfigure xserver-xorg to manually set driver as intel and not vesa and my LCD parameters with correct screen resolutions and voila, I am even having wobbly windows now! O:)

---

### Post by bryanagee on 2007-09-11
Worked beautifully for me; I had Beryl up and flying in about 15 mins. BTW Anyone else with this issue, my hardware id (in the Dell Vostro 200) is 29c2.

---

