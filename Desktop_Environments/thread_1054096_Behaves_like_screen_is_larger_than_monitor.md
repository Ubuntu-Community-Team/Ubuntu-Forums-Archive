---
title: "Behaves like screen is larger than monitor"
date: 2009-01-29
forum: Desktop Environments
---

### Post by scuicho on 2009-01-29
When I start up everything is fine however if the machine is left alone for more than 10 or 15 minutes the display will move to the right and down with the mouse as if it were much larger than the screen however it just moves into black space. I have checked and the resolution is correct so im not sure what is going on. Thanks in advance.

---

### Post by Yashiro on 2009-02-07
Does this occur when your screensaver or monitor shutdown should be triggered?

Disable your screensaver and set the monitor to never shutdown.
Also try running the following in a terminal: 
> xset s off
xset dpms 0 0 0
xset -dpms

---

### Post by Yashiro on 2009-02-09
The reason why this happens is that on some Ati drivers, triggering DPMS brings secondary displays online. Even if you don't use them.

This leads to weird issues as it tries to span your desktop over a non existant display.

Disabling the extraneous display device in the aticonfig panel will fix it without a reboot.

---

### Post by scuicho on 2009-03-13
Thanks worked like a charm!

---

