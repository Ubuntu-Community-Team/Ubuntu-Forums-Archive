---
title: "turning on radeonhd drivers under Ubuntu 32bit Intrepid"
date: 2009-03-14
forum: Desktop Environments
---

### Post by einfeldt on 2009-03-14
hi,

I am having troubles with flicker on my Intrepid (GNOME) system.  I am using a 19 inch CRT monitor and here is my video controller card from lspci:

VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

My screen resolution is 1024 x 768, but when I go to

System > Preferences > Screen Resolution

I see that the refresh rate is zero!  No joke!  There is also no opportunity to choose a different refresh rate with that Screen Resolution tool, and I have been told that Intrepid does not use the file

/etc/X11/xorg.conf

and so modifying that file will not work.

I have installed these drivers:

xserver-xorg-video-radeonhd
xserver-xorg-video-radeonhd-dbg

As suggested by this page:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

But apparently I need to somehow "turn on" those drivers, and I am not sure how to do it.  Any tips welcome.  Thanks!

---

