---
title: "KDE doesn't start anymore"
date: 2014-09-24
forum: Desktop Environments
---

### Post by uqbar on 2014-09-24
After last upgrade, KDE is not starting anymore.
I reach the KDE blue logo (with the rotating gear) and then just a black screen with the mouse pointer in the center.
startkde says KDE is already running. And in fact a number of KDE-related processes is running:
kdeinit4, kwin, krunner etc.
From commandline (on VT1) I ran "DISPLAY=:0.0 qdbus" and got a connection refused to /tmp/dbus- Oo97M9Gl6U.
This file/directory/socket doesn't exist at all!!!

I'd need a starting point for troubleshooting as the searches done so far seems to be inconcludent.
TIA

---

### Post by xc3RnbFO8P on 2014-09-25
Did you try:
> export $(dbus-launch)

---

