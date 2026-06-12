---
title: "Acer sis video and screen flicker with dpms suspend"
date: 2008-12-13
forum: General Help
---

### Post by maestrobwh1 on 2008-12-13
This is kind of odd.

I have an older Acer Aspire laptop.  When dpms activates per the set time in system settings, I can see a faint flicker at a regular rate.  Aspire 3005 LCi

Duplicated using:

xset dpms force suspend

or

xset dpms force standby

force off does nothing on this display.

I fear that the cycling is harder on the back light than just having it on all the time.

Is this a bug and is there a workaround?

---

### Post by maestrobwh1 on 2009-02-07
bump

---

### Post by HavocXphere on 2009-02-07
Kind vague to be honest. Flicker as in ever 2 seconds or multiple times per second?

If ~2 sec then you can try switching off the Detecting RandR screen changes under the services manager.

If its faster then I'd suggest first checking the refresh rate. Some LCD screens do weird stuff if you boost the Refresh Hz above 60. It's probably something like this:
[http://www.nvnews.net/vbulletin/showthread.php?t=26374](http://www.nvnews.net/vbulletin/showthread.php?t=26374)

Try forcing the refresh in your xorg using gtf.

---

