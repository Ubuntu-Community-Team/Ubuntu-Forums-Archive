---
title: "Compiz animations and Thunderbird tooltips"
date: 2009-04-27
forum: Desktop Environments
---

### Post by FokkerCharlie on 2009-04-27
Good afternoon from Cheshire!

I've recently upgraded my setup to Jaunty, and with it (I think) came the latest Thunderbird version 2.0.0.21 (20090409).  It's all very well, but I am seeing unwanted open/close animations on tooltips.

I don't get such animations on any other app's tooltips, as I have !(type=tootltip) (amongst other things) in the window match field in compiz settings.  So, why do I see it in Tbird?  Is it a Tbird bug (I think it probably is).  Has anyone else observed this?  Is there a workaround?

Thanks in advance!

Charlie

---

### Post by imaginaryboy on 2009-12-03
I just found this myself.

There is a workaround, the "Firefox Menu Fix" in the workarounds will prevent those from getting any animation.

It's also possible to write a rule that wouldn't match tooltips, even without the workaround, i.e.

  class=Thunderbird-bin & override_redirect=0

---

