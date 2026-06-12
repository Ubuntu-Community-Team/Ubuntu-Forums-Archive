---
title: "set primary monitor in jaunty"
date: 2009-05-08
forum: General Help
---

### Post by mooball on 2009-05-08
Im trying to set my primary monitor in jaunty 9.04 but I cant work out where to do so. The new Display UI is great for managing two monitors but it provides no way to specify which is the primary one. On my laptop it seems to keep setting the external monitor as the primary and puts the login screen and menus on it but Id prefer them to be on my laptop monitor.

Ive looked at the xorg.conf and its pretty much empty so it seems the settings have moved out of xorg.conf to somewhere else but I dont know where.

---

### Post by rduke15 on 2010-05-03
Same problem for me. Anybody has a hint / link / solution ?

---

### Post by dino99 on 2010-05-03
> **rduke15 said:**
> Same problem for me. Anybody has a hint / link / solution ?

which ubuntu ?
is your video recognized ?  (system admin hardware driver)

---

### Post by rduke15 on 2010-05-03
> which ubuntu ?

As the subject suggests: Jaunty 9.04

> is your video recognized ?  (system admin hardware driver)

No apparent driver problem. Everything works, including dual monitors, except that, like the original poster, I find no way to make the laptop display be the primary. When I connect an external monitor, it becomes the primary.

(
Thinkpad x200s
Intel video: dmesg shows "agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset".
And in case it's relevant:
$ lsmod |grep agp
intel_agp              34108  1
agpgart                42696  3 drm,intel_agp
)

---

### Post by rduke15 on 2010-05-03
In fact, I just realized that the real problem seems to be that I cannot have the external monitor on the left.

**The primary monitor is always the left monitor.**

Is there any way to let the right monitor (or a specific monitor, regardless of it's relative position) be the primary?

---

