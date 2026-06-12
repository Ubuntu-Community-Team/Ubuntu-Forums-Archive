---
title: "Display woes"
date: 2010-02-11
forum: Desktop Environments
---

### Post by Bob Harte on 2010-02-11
I'm not even sure what terms to search on, so I'm creating a new thread.

I just installed Ubuntu on an emachines pc about thrity minutes ago.  When I put the installation disk in, the screen was off center, to the left.  Roughly the left one inch (2.54 cm) was not visible.  On the right side of the screen, the rightmost inch (2.54 cm) was black.  It looked like I just needed to drag everything to the right about an inch.  

I hoped that this situation would correct itself after the install was complete.  It did not correct itself.  

I played around with the display settings.  I decreased the resolution from 800x600 to the next resolution down, 640x480?.  At the lower resolution, everything is centered, but now all of the screens appear to hang below the monitor.  As an example, I cannot change the monitor resolution back to the highest setting (800x600), because the bottom of the screen is below the bottom of the monitor.  I cannot see the 'apply' button.

Any ideas what to do about this?  The monitor is a 17 inch flat panel monitor that is probably six years old.

Thanks In Advance,
Bob

---

### Post by efflandt on 2010-02-11
I assume you are using a VGA cable, because a digital connection (DVI/HDMI) would usually be spot on for centered native resolution.  Does your monitor have any menu to adjust size/position or timings.  Some VGA monitors do that automatically, but one monitor I had only did that momentarily when you select Auto from its menu.

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) gives examples how to find/test modes that your monitor is capable of, but not recognized.  But that is not necessarily centered.

Also see **man xvidtune** which may help adjust a modeline to position the image like you want it.  Once you find a modeline that works, someone should be able to help you set that to be automatic.  I am not familiar with xorg.conf settings because that file does not exist unless created in 9.10.  But for a laptop sometimes connected to HDTV, I wrote a bash script to set that mode and turn of the laptop display.

---

### Post by Bob Harte on 2010-02-11
Thanks for your quick reply.  I was able to get the display centered by playing with the buttons on the monitor.  

I'm playing with the xrandr stuff that you gave me a link to now, trying to get it to recognize 1024x768.

Bob

---

### Post by Bob Harte on 2010-02-11
Thanks again for your help.  

When in doubt, RTFM.  It was in the beginner's guide to Ubuntu.

System > Administration > Hardware Drivers.  There was a driver for my video card.  It works fine now.

Bob

---

