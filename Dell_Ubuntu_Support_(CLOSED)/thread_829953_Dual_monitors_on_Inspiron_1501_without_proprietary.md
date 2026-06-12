---
title: "Dual monitors on Inspiron 1501 without proprietary drivers"
date: 2008-06-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xaprb on 2008-06-15
I've upgraded my Inspiron 1501 to 8.04 and got dual monitors working, but only with the proprietary drivers.  This sucks.  The proprietary drivers don't work with Compiz, they don't let me suspend or hibernate, and they crash when I switch to a virtual terminal and back again.  And I had to do a bunch of things to keep my Xorg logs from growing to gigabytes of messages about deadlocks.

Proprietary drivers suck.  I suck for buying a laptop that has hardware whose vendors don't support Free Software.  But I digress.

Is there any way to get this working with the radeon (open-source) driver?

It seemed that the driver recognized that I had an external monitor (in my case a 1280x1024 LCD) plugged in, but the best I could get was to have the display mirrored on the two monitors, rather than extending my desktop across both monitors at once.  Oddly, all the settings I changed in my xorg.conf seemed to be ignored -- every time I started X, I got the same thing no matter what changes I put into the xorg.conf.  Only when I switched to the proprietary driver did the settings seem to have any effect.

---

