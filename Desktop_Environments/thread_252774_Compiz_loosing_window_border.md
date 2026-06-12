---
title: "Compiz loosing window border?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Stelmate on 2006-09-07
Okay I'm trying to see why this is happening.  I'm starting compiz with the following
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize
 cube rotate zoom scale move resize place switcher &

and when I do, if I click on a maximized windows then I will lose the window border up on top.  (So of course I have to right click on it just to minimize the window which is driving me crazy).  Does anyone know of any fix for this?  I'm using the most recent version of compiz.

---

### Post by ayoli on 2006-09-07
the most recent compiz version should be launched with 
```
/usr/bin/compiz-start
```
to enable/disable plugins and settings run:
```
/usr/bin/csm
```

---

