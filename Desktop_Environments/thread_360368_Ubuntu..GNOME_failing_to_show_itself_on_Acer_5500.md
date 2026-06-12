---
title: "Ubuntu..GNOME failing to show itself on Acer 5500"
date: 2007-02-13
forum: Desktop Environments
---

### Post by esumitkumar on 2007-02-13
Hi 

I have Acer 5500 having Pentium M 1.73 Mhz , ATI Radeon X 700 card . Yesterday I installed Ubuntu from its 3.5 GB DVD but its not showing GNOME desktop...it starts, then screen becomes black. I edited file xconf.org ...but there file has clearly a entry of "ati".

I again reinstalled Ubuntu to solve the mess. It is taking default of 1024*768,800*600 and 640*480 resolutions... Still GNOME isnt able to show itself

The same Ubuntu is working fine on my desktop (AMD 3600 + Nvidia 6150 Inbuilt) 

Please Ubuntu users ...Help me.......:confused:

---

### Post by renzokuken on 2007-02-13
open up your xorg.conf again and replace "ati" with "vesa"..............save, reboot, then you should have gnome working....

then you can look into installing the fglrx drivers (proprietry linux ati driver). i would recommend doing this with Envy by tseliot [www.albertomilone.com](www.albertomilone.com) and look in the projects and guides section

---

