---
title: "GNOME Shell Remix: Nautilus CoreDumps"
date: 2012-10-21
forum: Desktop Environments
---

### Post by mpmistr on 2012-10-21
When I run Nautilus from Terminal I get..

(nautilus:3026): Gdk-CRITICAL **: gdk_x11_display_get_xdisplay: assertion `GDK_IS_DISPLAY (display)' failed
Segmentation fault (core dumped)

This happened after the recent update to Nautilus in the Gnome3 Team PPA.. any idea what is going on? :confused:

---

### Post by 0verm1nd on 2012-10-22
This happened to me as well. I don't know the cause of it, but I reverted to a previous version via synaptic until someone smarter than I fixes it.

Not exactly a fix, but at least you'll be able to access your files.

---

### Post by mpmistr on 2012-10-22
> **0verm1nd said:**
> This happened to me as well. I don't know the cause of it, but I reverted to a previous version via synaptic until someone smarter than I fixes it.

Not exactly a fix, but at least you'll be able to access your files.

I believe this has been fixed. There was a new Nautilus package uploaded this morning.

---

