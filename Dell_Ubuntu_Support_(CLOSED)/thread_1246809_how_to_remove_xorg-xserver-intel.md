---
title: "how to remove xorg-xserver-intel"
date: 2009-08-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by greyfoxsylux on 2009-08-22
the package xorg-xserver-intel is giving me many roadblocks in my ability to do things. I wish to do automatic updates, but the package would ruin it.

Any way to completely remove it from being able to be downloaded/upgraded without affecting other crucial packages?

I have a DELL Inspiron 4000 with ATi Mobility M3, and I have my xorg.conf the way I want it, and by installing that package, it messes everything up.

Please help me out on this one.

---

### Post by ajgreeny on 2009-08-22
Just pin the version you are running at the moment with synaptic.  It's in the **Package> Lock Version** menu item.  You will not then be asked to update that package again.  You can do this with the cli as well by editing the file
/etc/apt/preferences and adding
```
Package: xorg-xserver-intel
Pin: version (enter your working version)
Pin-Priority: 1001
```

---

### Post by greyfoxsylux on 2009-08-22
Thank you, hope this would fix the issue. This driver has driven me up the wall, and maybe I can finally rest in peace.

Thank you ajgreeny, much appreciated and many thanks.

One more reason to rely on the handiness of Linux. Always a solution to a problem.

---

