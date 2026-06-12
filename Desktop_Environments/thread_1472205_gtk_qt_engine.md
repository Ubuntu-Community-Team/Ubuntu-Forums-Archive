---
title: "gtk qt engine"
date: 2010-05-04
forum: Desktop Environments
---

### Post by wirate on 2010-05-04
I have gtk-qt-engine installed and kcmgtk configured to use qt style but still my gtk apps are same old gtk. suggestions?
screenshot attached so you can see

---

### Post by Zorael on 2010-05-06
All GTK apps or only apps started with superuser permissions? You show Synaptic as an example, and it's commonly started as root (for obvious reasons).

You can ensure that the QtCurve theming is done in root's apps, as well as transfer your current "global" KDE settings (theming, coloring, fonts, et al) by running the following commands in a terminal. Omit the dollar-sign.
```
$ sudo cp ~/.gtkrc-2.0-kde4 /root/
$ sudo cp ~/.kde/share/config/kdeglobals /root/.kde/share/config/
```

Tweak root's settings by starting System Settings with kdesudo. Hit Alt+F2 to spawn a run box, and then enter '**kdesudo systemsettings**'. Then into Appearance and whatnot.

---

