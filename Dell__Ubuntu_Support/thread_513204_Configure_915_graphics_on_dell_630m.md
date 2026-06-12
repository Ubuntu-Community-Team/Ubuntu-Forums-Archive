---
title: "Configure 915 graphics on dell 630m"
date: 2007-07-30
forum: Dell  Ubuntu Support
---

### Post by sun_radha on 2007-07-30
Hi,

I am totally new to linux, I have recently installed ubuntu on my dell 630m. 

The resolution 1024*768, I have downloaded the .deb pkg for 915 chipset  "xserver-xorg-video-intel_1.......**.deb" but when I tried to install, it conflicts with i810 driver so I did a remove on i180 "sudo apt-get remove xserver-xorg-video-intel". And now my system fails to install the new 915 chipset
and doesn't start x-windows. Says some problem with dependencies!!

Please Help

Thanks

Sun

---

### Post by fsckedagain on 2007-07-30
I have an xps m140 (the same laptop basically) and all I do with a vanilla install is open synaptec package manager and update it, then go to xorg-xserver-intel-video and select install, it automagically uninstalls thte other xorg driver and installs the right one for widescreen goodness. :)

---

### Post by cacycleworks on 2007-07-30
yeah, you'll need to apt-get install the core again... is simply xserver-xorg

that or dpkg-reconfigure xserver-xorg (which you need to do after installing i915)

do not tell it to detect/probe...

---

### Post by sciurus on 2007-07-31
> **sun_radha said:**
> 
The resolution 1024*768, I have downloaded the .deb pkg for 915 chipset  "xserver-xorg-video-intel_1.......**.deb".... And now my system fails to install the new 915 chipset
and doesn't start x-windows. Says some problem with dependencies!!

Did you download the version for Feisty (the current version of Ubuntu  which you most likely have installed) or Gutsy (the unreleased next version which is currently being developed)? If you downloaded the Gutsy version, it can't install because it depends on other software from Gutsy. If you downloaded the Feisty version, I'm not sure why it doesn't work, but you didn't need to download it. You could simply install it with sudo apt-get install xserver-xorg-video-intel.

---

### Post by stinkypudding on 2007-08-09
Do I stilll need the i915 resolution package, if I install the intel driver?   Or will the driver automatically set my resolution for widescreen?

---

### Post by cacycleworks on 2007-08-09
> **stinkypudding said:**
> Do I stilll need the i915 resolution package, if I install the intel driver?   Or will the driver automatically set my resolution for widescreen?

No need for 915, 

Here's my full install... everything works. No compiling, no confusion...

[http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702)

---

### Post by Mach1US on 2007-08-09
I have dell with 915 graphics and it works 100% fine with feisty which was automatically configured during installation.
Only problem i have had was with suspend and hibernation mechanisms which has been totally fixed by this how-to 
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)
Now all works 100% with  correct res .

---

