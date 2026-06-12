---
title: "[SOLVED] On/Off Compiz"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by Mongo5000 on 2007-09-19
Compiz works like a charm except when I need to use VNC to access my PC.  I just reboot without compiz starting up and it works.  I'm okay with his but is there a way I can turn off compiz fusion without having to reboot?

I know how to turn it on, but turning it off baffles me:confused:

---

### Post by martynp on 2007-09-19
Try This:

[http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/](http://tombuntu.com/index.php/2007/08/26/compiz-fusion-tray-icon/)

---

### Post by Mongo5000 on 2007-09-23
I tried the tray icon but it didn't seem to work properly.  It starts compiz properly but it won't shut it down at all.  Tried rebooting with it controlling compiz but no go.

Any other ways to turn off compiz fusion without having to reboot?

---

### Post by Forlong on 2007-09-23
Just open [Alt]+[F2] and type
```
metacity --replace
```
(GNOME)
```
kwin --replace
```
(KDE)
```
xfwm4 --replace
```
(Xfce)

---

### Post by Mongo5000 on 2007-09-26
> **Forlong said:**
> Just open [Alt]+[F2] and type
```
metacity --replace
```
(GNOME)
```
kwin --replace
```
(KDE)
```
xfwm4 --replace
```
(Xfce)

Awesome stuff.  Thx!

---

