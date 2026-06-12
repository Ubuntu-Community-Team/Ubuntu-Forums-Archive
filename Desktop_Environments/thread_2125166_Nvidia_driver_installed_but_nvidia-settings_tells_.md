---
title: "Nvidia driver installed but nvidia-settings tells I am not using it?"
date: 2013-03-13
forum: Desktop Environments
---

### Post by josm on 2013-03-13
I am using Ubuntu 12.10 64 bit.
lspci reports I have a "NVIDIA Corporation G98 [Quadro NVS 295] (rev a1)" graphics card installed. I wanted to use the second monitor (by default it only mirrors the main monitor which cannot be changed) so installed nvidia-settings. nvidia-settings told me that "i do not appear to use the NVIDIA driver" so I used "Software Sources" - "Additional Drivers" to choose the NVIDIA binary Xorg driver. After this, I tried again only to get the same message!
So although the binary driver (which is the recommended one) is installed, I am still unbale to use nvidia settings? Also graphics no does not work at all, the screen shows just a lousy low resolution, and Unity has stopped working so I can only use low-resolution XFCE to do anything.

All the pages I found so far are either about different hardware or for different Ubuntu version or want me to install something from a PPA which I would rather avoid. 

Is there anything known about this? I rather expected this to smoothlessy work out of the box without any fiddling around! :)

---

### Post by grahammechanical on 2013-03-13
I would suggest two things.

First, try a different Nvidia driver. Nvidia drivers have not been up to standard for a few months. You may need to experiment with what works best on your machine.

Second, reboot. May be you did this. I have found that once I used Additional Drivers to activate an Nvidia driver then Nvidia Xserver Settings also was installed as part of the deal.

Regards.

---

### Post by papibe on 2013-03-13
Hi josm,

If grahammechanical's suggestion doesn't work. Try running this:
```
sudo nvidia-xconfig
```
Then restart your computer.

In case that does not help either, please post the content of this file:
```
/var/log/Xorg.0.log
```
Paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the link to it.

Regards.

---

### Post by josm on 2013-03-13
Thank you everybody for your help. 
I did try not just the recommended driver but also the experimental ones (the additional driver dialog offers several). Does not make any difference.
Also, running "sudo nvidia-xconfig" was of course the first thing I tried because it is suggested in the error message shown by nvidia-settings. This does not make any difference either.

I have given up on this, because I figured out how to do what I originally wanted even with the standard (no-proprietary) drivers, both in Unity and XFCE (it is a bit harder in XFCE but possible). So I do not have a need for the prorpietary drivers any more - I though I can do this only with nvidia-settings.

---

