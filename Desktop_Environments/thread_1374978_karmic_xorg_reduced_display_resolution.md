---
title: "karmic xorg reduced display resolution"
date: 2010-01-07
forum: Desktop Environments
---

### Post by carolinason on 2010-01-07
My display properties only allow me to choose 1024x768. The native resolution of my LG Flatron W1952TQ is 1440x900. It was working fine until I hooked up a second monitor. 

I've unhooked the second monitor and still I am only able to select 1024x768.

I ran 
#> dpkg-reconfigure xserver-xorg 
it didn't work. I tried the completely uninstalling option xserver-xorg-video-radeon, xserver-xorg-video-all and xserver-xorg-video-ati and then reininstalling in synaptic, but this didn't work either.

Another note is that no matter how I set the screensaver or power management, the monitor will shutdown after 10 minutes.

This has happened before and I wound up reinstalling Ubuntu, but I think it's rather silly to do this when it should be an easy fix.

This used to be a simple edit in xorg.conf, but everything has changed. 

Any suggestions would be greatly appreciated..

---

### Post by carolinason on 2010-01-09
reloaded ubuntu, thanks!

---

