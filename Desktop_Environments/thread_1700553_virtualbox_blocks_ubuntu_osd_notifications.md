---
title: "virtualbox blocks ubuntu osd notifications"
date: 2011-03-05
forum: Desktop Environments
---

### Post by nETPOBu4 on 2011-03-05
Hello!
VirtualBox in fullscreen mode blocks ubuntu osd notifications. Is there a way to configure notifications to be shown anyway?

---

### Post by cprofitt on 2011-05-04
The same issue is apparent in 11.04 as well. Was a work around ever found?

---

### Post by nETPOBu4 on 2011-05-04
I digged deeper and find out more info about notifications. 
There are notification urgency levels: normal, critical, etc.
VirtualBox (and any another fullscreen app blocks all but critical 
notifications).
So if you need notification on top of fullscreen virtualbox session
just use critical urgency level.

There's a bug in notify-osd and dbus interface: you can't set urgency 
level via dbus.
I've opened ticket here:
[https://bugs.launchpad.net/notify-osd/+bug/729636](https://bugs.launchpad.net/notify-osd/+bug/729636)
Test it and click "it affects me too" it so.

Python and c interfaces don't affected (it seems).

---

