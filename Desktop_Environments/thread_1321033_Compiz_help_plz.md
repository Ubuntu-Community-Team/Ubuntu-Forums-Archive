---
title: "Compiz help plz"
date: 2009-11-09
forum: Desktop Environments
---

### Post by demorik on 2009-11-09
Hey wuzzup guys, im new to this forum and linux overall, i just got a question about compiz, ive got it enabled and running in 9.04 all effects work and such but how do you get it fully integrated into the desktop such as when u click " applications'' it opens with the compiz effect ive selected for opening windows, ive seen vids of ubuntu and they all do this. Am i missing something?

---

### Post by stinkeye on 2009-11-10
> **demorik said:**
> Hey wuzzup guys, im new to this forum and linux overall, i just got a question about compiz, I've got it enabled and running in 9.04 all effects work and such but how do you get it fully integrated into the desktop such as when u click " applications'' it opens with the compiz effect ive selected for opening windows, ive seen vids of ubuntu and they all do this. Am i missing something?
Install compizconfig-settings-manager to customize your effects.
CCSM > effects > animations.
Also install fusion-icon and place it in your startup applications.
Type```
fusion-icon -n
``` in the command box of startup applications.
This will load fusion icon at start but the -n option stops it from trying to load a window manager because some people have problems with this.
fusion-icon sits in the notification area and gives you quick access
to compizconfig-settings-manager as well as other settings.

---

### Post by demorik on 2009-11-10
Thanks i will try that later.

---

