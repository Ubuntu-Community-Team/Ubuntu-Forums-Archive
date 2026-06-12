---
title: "xorg.cofig removed."
date: 2009-12-31
forum: Desktop Environments
---

### Post by CO_Shifty on 2009-12-31
Hello everyone, I recently gave up my nvdia 8800 gts for an ati radeon x1900 xt.
I had the misforutune of not knowing it was not longer supported by the ati linux driver, but decided to stick with it.

Anyways, the default xorg.config had a low color depth and all of compiz fusion eye candy was disabled, but when I deleted xorg.config all of the eye candy came back, and I had an excellent color depth.

I am wondering how is it possible for xorg.config to be missing, and yet be better? Is there a drawback to this, an is there a reason to put it back?

---

### Post by Seq on 2009-12-31
X.org can probe hardware as needed. If you specify things in xorg.conf, it overrides whatever it may probe.

The only time you need an xorg.conf is if you're changing something from defaults (for me, using the nvidia driver instead of nv).

---

