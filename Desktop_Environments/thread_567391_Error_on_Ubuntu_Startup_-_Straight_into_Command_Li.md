---
title: "Error on Ubuntu Startup - Straight into Command Line"
date: 2007-10-04
forum: Desktop Environments
---

### Post by phargarten on 2007-10-04
I just installed the most recent nvidia drivers and now the gui wont load. I can change the driver back to "nv" in xorg but I cannot revert back to my old working driver in Fiesty. Help Please!!

HP Dv2000t 
Ubuntu 7.04 
Nvidia GeForceGo 7200 PCI-E

Attempted install of the recent 100 series nvidia driver from their website

I cannot get the error code.

---

### Post by benerivo on 2007-10-04
When you installed your new driver, it may have removed the old one. Try ```
sudo aptitude install nvidia-glx-new
```and maybe also ```
sudo nvidia-glx-config enable
```and then check that it's using nvidia in xorg.

---

### Post by dinub1 on 2007-10-04
> **benerivo said:**
> When you installed your new driver, it may have removed the old one. Try ```
sudo aptitude install nvidia-glx-new
```and maybe also ```
sudo nvidia-glx-config enable
```and then check that it's using nvidia in xorg.

This reply is inteended to the original poster. 

You can also try reconfiguring xorg to auto detect the video card that you have and adjust the video modes for you.
Type:

$sudo dpkg-reconfigure xserver-xorg

And then follow the screen intructions. Hope this helps.

---

