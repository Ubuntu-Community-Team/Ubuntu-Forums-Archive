---
title: "How to make OpenOffice 3 fonts consistent with Gnome?"
date: 2008-11-14
forum: Desktop Environments
---

### Post by softtower on 2008-11-14
I really like to set font hinting to slight and enable anti-aliasing: this gives me very contrasty, somewhat "beefy" fonts that I love Linux for.

I've had Ubuntu 8.04 configured this way and I had beefy fonts even in my gnome login panel, where you type your username/password. Then I installed OpenOffice 3.0 and it inherited those settings. It was awesome.

Now I installed 8.10 (Intrepid) from scratch on a new laptop, adjusted font hinting to slight in Gnome and also in ~/.fonts.conf, installed OpenOffice 3.0 but it did not pick my "slight hinting" setting. Moreover, my Gnome login panel also ignores my font rendering configuration. Both (OO and Login panel) appear to be using "full hinting, no subpixel smoothing" method.


I also ran dpkg-reconfigure fontconfig-config and selected native hinter and set "sub-pixel" to always: that didn't do anything.

Where do I force OO to use my font settings?

---

### Post by Prosis on 2008-11-21
Yeah I'd like to know that too!

---

