---
title: "Desktop doesn't fit screen"
date: 2009-07-21
forum: Desktop Environments
---

### Post by Argyris1984 on 2009-07-21
My desktop doesn't fill up the entire screen, there is about an inch of black on both sides of the desktop that is black from top to bottom. I have seen tons of things about trying to use the xorg.conf, but am really new to Ubuntu so not sure where that is. Also I have tried all the settings in the display and none have fixed it.

Thanks

---

### Post by Canuckelhead on 2009-07-21
do you have the refresh rate set correctly?  When I use my netbook on an external screen I always miss that and get a smaller screen...

---

### Post by Argyris1984 on 2009-07-21
I should have mentioned but didn't think of it, that this started after I hooked my laptop up to another monitor, when I removed the other monitor my screen was stuck in a small screen as I described earlier.

---

### Post by Zorael on 2009-07-22
Is it a problem even at the login screen, or does it start once you've logged in? Are you running Jaunty, and if so, did you do a fresh install or did you upgrade from an earlier version?

Optimally you should have a fairly empty or even nonexistent xorg.conf, which for the record is located in **/etc/X11/**. At X startup it will poll your monitor and videocard for their available resolution modes (and even the monitor's physical size to an extent). Remnant or malconfigured options in your xorg.conf may just come inbetween this and mess stuff up.

For the average user, the only thing you need xorg.conf for is to enable proprietary drivers, such as Nvidia's display driver.

So, please post the contents of your **/etc/X11**/xorg.conf file.

---

