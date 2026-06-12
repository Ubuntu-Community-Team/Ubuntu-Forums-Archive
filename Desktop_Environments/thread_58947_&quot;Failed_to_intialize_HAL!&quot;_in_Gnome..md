---
title: "&quot;Failed to intialize HAL!&quot; in Gnome."
date: 2005-08-22
forum: Desktop Environments
---

### Post by BanskuZ on 2005-08-22
When I boot into Gnome, I will get text "Failed to intialize HAL!". Fluxbox works fine.

Ubuntu 5.04

---

### Post by Tuxhedoh on 2005-08-22
I received this error message yesterday after messing around with xcompmgr  I rebooted and the problem went away.  I imagine you already did this though.

---

### Post by Dolphin on 2005-08-22
I'm sorry I can't do that Dave.

<had to be done> :)

---

### Post by skoal on 2005-08-22
For whatever reason it occurs now, until it can be fixed, you can run the dbus-1 init script to restart the hald:

sudo /etc/init.d/dbus-1 start

or just run the hald script directly:

sudo /etc/dbus-1/event.d/20hal start

Then, just log back out and back into Gnome...

\\//_

---

