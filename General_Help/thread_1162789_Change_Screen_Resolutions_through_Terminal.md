---
title: "Change Screen Resolutions through Terminal"
date: 2009-05-18
forum: General Help
---

### Post by raziiq on 2009-05-18
Hi there.

Can somebody please tell me how to change the screen resolutions through a terminal command??

---

### Post by Bindsa on 2009-05-18
Type this in terminal, replace [resolution] with your resolution:
```
xrandr -s [resolution]
```
E.g.:
```
xrandr -s 1024x768
```

---

### Post by WakkiTabakki on 2009-05-18
Check out xrandr ([http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)). Depending on what graphics card you have, it may or may not work properly...

/N

---

