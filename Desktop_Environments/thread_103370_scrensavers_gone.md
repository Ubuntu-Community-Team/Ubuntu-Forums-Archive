---
title: "scrensavers gone"
date: 2005-12-14
forum: Desktop Environments
---

### Post by Akya on 2005-12-14
when i go through my screen savers some say not installed how do i install them? and does any one know of any kick ass screen savers?

---

### Post by hda on 2005-12-14
Some screensavers require additional packages to be installed, e.g. xearth, xdaliclock, etc. In most cases you can easily find out by typing (in a console window)
```
apt-cache search <name of screensaver>
```

The *kick ass screensaver* of your choice depends on what you prefer. Screensavers nowadays don't really *save* your monitor, so the *blank screen* and *DPMS off* options are best considering performance. If you want some fancy saver check out the GL savers. Some of them are simply beautiful and don't require too many CPU cycles if used on hardware accelerated graphics equipment.

_hda_

---

### Post by Akya on 2005-12-16
i just want some really amazing looking ones and just cool stuff and how do i install them after doing that apt-cache thing?

---

### Post by hda on 2005-12-16
If you found out the name of the package you simply install it with, e.g.
```
apt-get install xdaliclock
```

---

