---
title: "Resolution limited to 1024x768"
date: 2009-01-05
forum: General Help
---

### Post by Hunsrus on 2009-01-05
Gentlemen,

The first time I booted Ubuntu, it ran in a nice and clean resolution of 1280x1024, it being the resolution I prefer. However, when I install the non-free hardware driver for my Nvidia GeForce 7900 GTX (v 177, but I've had the problem before) the resolution gets limited to 1024x768.

I've looked into Preferences -> Screen resolution, but it's limited there. I've also looked into the X server config GUI, and it seems to give me the options for resolutions somewhat higher than 1024x768, but I can't seem to apply them.

In previous versions of Ubuntu I was succesful using "Displayconfig-gtk", however in 8.10 this tool is no longer available. My Xorg file just shows "Default monitor" and "Default device" on everything, which strikes me as it not recognizing my monitor.

Best regards,

Hunsrus

---

### Post by gettinoriginal on 2009-01-11
It depends how you installed your nvidia driver.  First, make sure you have "ubuntu-restricted-extras installed, then System > Admin > Hardware Drivers, and let the computer pick which one you need :p

---

