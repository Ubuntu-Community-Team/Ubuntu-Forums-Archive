---
title: "I have Ubuntu but after installing Kubuntu desktop computer freezes"
date: 2016-04-13
forum: Desktop Environments
---

### Post by His on 2016-04-13
I currently have Ubuntu and it's mostly stable. I tried installing kubuntu-desktop and after reboot my computer completely freezes. The only way I found out of it was to do alt+sysrq REISUB. The only way I could actually get into my computer was by booting into single user mode. I didn't bother trying to fix it because I wanted to repartition my HDs anyway, so I took that opportunity to repartition and reinstall. I should have pulled some logs, but oh well.

So now, here I am, a mostly clean install of Ubuntu and really want to try KDE though I'm worried about how that install is going to go. 

Basic hardware info:
Processor: 4x Intel(R) Core(TM) i5-6600K CPU @ 3.50GHz
Memory: 8125MB (1353MB used)
Operating System: Ubuntu 15.10
Display
OpenGL Renderer: AMD Radeon (TM) R9 380 Series using fglrx-updates.
X11 Vendor	The X.Org Foundation
Multimedia
Audio Adapter	HDA-Intel - HDA Intel PCH
Audio Adapter	HDA-Intel - HDA ATI HDMI

Any thoughts about what happened or any suggestions to try installing it safely? Should I just do kde-full instead of kubuntu-desktop?

Thanks!

---

### Post by T.J. on 2016-04-14
It is just my opinion, but KDE Frameworks 5 has always been horribly buggy and unstable on my AMD video card, AMD FGLRX driver or not.  KDE 4 was much the same way for a couple of years after the first release.

That is not to say that the FGLRX driver doesn't have bugs.  I've personally noted bugs in it going back years that have never been corrected.  AMD has depreciated the driver and 16.04 can't even use it.  As you have an R9, you will be able to use the new AMDGPU driver, when 16.04 is released. 

If you want some advice?  I would install Xubuntu, as it is far more stable than KDE.  After you install it, you can use apt-get to install kubuntu-desktop and kde-full.  If the KDE install goes south on you again, you can use XFCE until 16.04 is released.  Hopefully, 16.04 will work better for you.

---

### Post by jay_bowles2 on 2016-04-17
I think that you need to install the AMD proprietary drivers for this issue as other than that your hardware looks okay. Unfortunately, with 16.04 release coming up next week, these drivers will not be installable on release, nor for quite some time afterwards (there will be other posts mentioning this) so it looks like you may be out of luck with Kubuntu for a while. The other option is to try another distro that has good KDE support. openSUSE is a good one, although they are a little different in the way they do things. Also Kaos is another excellent distro which is purely based one kde plasma. Worth a look if you want to check out what KDE has to offer.

 As for KDE plasma being buggy, I personally haven't had any issues. However I do have an Nvidia card....

---

