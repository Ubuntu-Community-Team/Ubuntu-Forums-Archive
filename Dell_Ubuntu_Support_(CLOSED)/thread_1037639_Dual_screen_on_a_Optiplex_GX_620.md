---
title: "Dual screen on a Optiplex GX 620?"
date: 2009-01-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bolddesign on 2009-01-12
I'm  running Ubuntu 8.10 @ work and the main screen is reconized fine as its an ATI 7200, but the main gfx card off the mother isn't working @ all. How can I use it for dual screens?

---

### Post by linux_tech on 2009-01-12
Has the onboard worked before?

Check config-
```
gksu displayconfig-gtk
```

what is output of 
```
lspci | grep -i vga

```
```
xrandr
```

---

