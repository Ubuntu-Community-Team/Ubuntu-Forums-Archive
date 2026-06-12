---
title: "Please help with the screensaver (realy annoying problem)!"
date: 2009-11-14
forum: Desktop Environments
---

### Post by liquid77 on 2009-11-14
I have this really annoying problem with the screensaver.. I have deactivated the screensaver from the system settings (Desktop->screensaver) but it keeps starting and locking the screen (asking for password to unlock) every almost 1 minute.It doesn't seem to be deactivated in any way I have tried( I also edit the screensaverrc file in my ~/.kde/configure folder)..Please can someone tell me how I can completely deactivate the screensaver!! Is any other way except from the system settings (which doesn't seem to work)?

---

### Post by kellemes on 2009-11-14
Can it be you use xscreensaver?

From terminal..
```
xscreensaver-demo
```

---

### Post by liquid77 on 2009-11-14
I removed xscreesaver for that reason but the problem insists.It is a screen saver from the kscreensaver collection..The bad thing is that the screensaver starts not only when the computer is idle but also when you use it...:confused:

---

### Post by vachev on 2009-11-15
if you have a nvidia card like me, it is the "powermizer monitor" in
nvidia-settings -> nvidia-settings Configuration ->PowerMizer Monitor (GPU 0)
just uncheck the box
info: [http://www.nvidia.com/object/feature_powermizer.html](http://www.nvidia.com/object/feature_powermizer.html)

---

