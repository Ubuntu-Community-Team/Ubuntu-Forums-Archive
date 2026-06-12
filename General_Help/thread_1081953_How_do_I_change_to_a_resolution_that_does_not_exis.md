---
title: "How do I change to a resolution that does not exist in settings?"
date: 2009-02-27
forum: General Help
---

### Post by DarkBabar on 2009-02-27
I have a monitor with recommended resolution 1280*1024, but the highest resolution available in Preferences -> Screen Resolution is 1024*768. In olden days I would've just edited /etc/X11/xorg.conf, but nowdays you're not supposed to do that. I've tried booting into repair mode and running xfix, but to no avail. Some help would be appreciated.

---

### Post by Peter09 on 2009-02-27
the command ```
xrandr
``` may help but I have had little success.

try
```
xrandr -h
``` for help

---

### Post by DarkBabar on 2009-02-27
This did the trick, so thank you.
```
xrandr --auto
```

---

