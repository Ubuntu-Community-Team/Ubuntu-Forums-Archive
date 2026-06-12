---
title: "Xorg EATS cpu resources."
date: 2005-03-16
forum: Desktop Environments
---

### Post by fackamato on 2005-03-16
Hoi, using hoary, xorg, and the latest nvidia driver from their site (released this month). 3D is working wonderful, but if I have a terminal open with top started I get tremendous cpu usage just moving a window around, see the screenshots at [http://www.tehjunkyard.net/configs/cpuusage/](http://www.tehjunkyard.net/configs/cpuusage/) .

dmesg, xorg logfile, glxinfo and xorg config at [http://www.tehjunkyard.net/configs/](http://www.tehjunkyard.net/configs/) .

I have a GeForce 3 Ti200, using the kernel's AGP driver on a i875 chipset, on kernel 2.6.10-5-686-smp (HT enabled P4).

Any idea on this? :/

---

### Post by daniels on 2005-03-16
One word: Composite.  That's the reason why it's not enabled by default.

---

### Post by fackamato on 2005-03-16
[QUOTE=daniels]One word: Composite.  That's the reason why it's not enabled by default.[/QUOTE]

It's not enabled in my config. But I uncommented "composite enable" and changed it ti disabled, I'll see what happens.

**edit:** Nope, didn't solve it. I'm definitly not using the composite extension, but still xorg eats 100% cpu while for example resizing a gnome terminal. glxgears gives me good 2300fps.

From the xorg log:

```
(**) Extension "Composite" is disabled
(**) Extension "RENDER" is enabled

(snip)

(II) Initializing built-in extension COMPOSITE
```

Hm.

---

