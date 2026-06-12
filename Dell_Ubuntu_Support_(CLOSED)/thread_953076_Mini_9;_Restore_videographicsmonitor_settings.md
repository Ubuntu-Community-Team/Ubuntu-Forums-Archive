---
title: "Mini 9:; Restore video/graphics/monitor settings?"
date: 2008-10-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by gavinfoxx on 2008-10-19
How do I restore the default graphics/ video card / monitor / video settings and drivers with my ubuntu mini 9?  Or, failing that, get the most optimal or recent settings?

P.S. Forgive me if this was a double post.

Also, I seem to have somehow greatly slowed my computer down... and I can't diagnose why...

---

### Post by mknell on 2008-10-20
Yeah, I've run into the same problem - and by using "Screens & Displays" (displayconfig), I've managed to muck up the x11.conf and none of the previous versions have the 1024x600 setting.  They're all it's missing the default resolution / settings for 1024x600

Any Ubuntu vets or follow Inspiron Mini 9 owners care to share some wisdom for a relative Ubuntu newb? :)

Thanks.

---

### Post by mdroach on 2008-10-21
I messed my mini display up when I tried to drive a second monitor. I was able to fix it by editing /etc/X11/xorg.conf and setting the display resolution to 1024 600 under Screen Display Virtual and then rebooting.

---

### Post by gavinfoxx on 2008-10-27
Uh, I got it fixed... somehow. I think it involved manually choosing the experimental intel drivers.

---

