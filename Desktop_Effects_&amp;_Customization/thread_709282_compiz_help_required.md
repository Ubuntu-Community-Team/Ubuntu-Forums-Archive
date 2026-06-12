---
title: "compiz: help required"
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by mavr on 2008-02-27
Here is my situation. I've got a celena running at the moment (linuxmint) with beryl working like a charm. I only had to change my colour depth to 16 from 24 because my card cannot run at 1400x1050 otherwise.

Now i am testing the 7.10 live cd but i don't seem to be able to get any desktop effect. When running compiz from terminal it say:
no glxfbconfig for default depht
this is not going to work

I wanted to try to fix this on the live before spending time installing.
I am on a travelmate 650 with a radeon mobility 7500.

---

### Post by Afkpuz on 2008-02-27
Ati cards generally need xserver-xgl installed to run compiz.  I don't think that you will be able to get effects from the live CD, but a real install should only require xserver-xgl and the restricted driver to get effects.

---

### Post by Yellow Pasque on 2008-02-27
ATI proprietary drivers do not support cards earlier than the radeon 9500.

The effects should work with the open-source driver. Please post the /var/log/Xorg.0.log file.

---

