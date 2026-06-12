---
title: "Dual-monitor issues (random screen blanking) with nVidia Quadro NVS 290"
date: 2011-02-23
forum: Desktop Environments
---

### Post by codebrewery on 2011-02-23
I recently upgraded my 10.04 installation to 10.10 and ever since my dual monitor set-up has been behaving oddly - my secondary monitor randomly goes black for a second and then comes back as normal. I've tried to reproduce it with no luck and it isn't something I experienced with previous installations so wondered whether it's a known problem with 10.10?

---

### Post by Krytarik on 2011-02-23
I experienced the same behaviour in Windows when I set up the dual monitor config for both OSes at my mom's system. The cause solution there was to set the refresh rate to 50Hz instead of 60Hz (default), although Ubuntu runs the monitor fine with 60Hz.

Follow this guide to check this:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Richard Mathie2 on 2011-09-22
same happening here, I just updated the driver and it started happening, only occours on the second monitor, I think it happens whenever something new is loaded onto the screen/card , i.e. a you tube video starts to play or you look at the GLX info in the nvidia setting panel

very strange

---

