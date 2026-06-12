---
title: "Gnome-panel Compiz button for touchscreen"
date: 2010-08-30
forum: Desktop Environments
---

### Post by reckik on 2010-08-30
Hi all,

Im looking for a way to add a button too my gnome-panel for a compiz plugin action. Is there a gnome-applet or something that does that?

example..
win+E initiates the expo plugin for compiz, and add a button for that on the gnome-panel?

thx
harm

---

### Post by freeball1 on 2010-08-30
You can use [xte]("http://linux.die.net/man/1/xte") (should be in package xautomation).
For example set expo initiator to F12 in ccsm and add a custom application launcher to your panel with this command: 
```
xte "key F12"
```

---

