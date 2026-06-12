---
title: "Gnome freezes after log in"
date: 2011-02-07
forum: Desktop Environments
---

### Post by gruppler on 2011-02-07
I'm not sure exactly when this started happening, but it was probably after an update. My laptop boots up just fine, GDM starts, I log in, most of the Gnome panel's contents load, and then everything just freezes. The mouse still moves, but nothing is interactive. Sometimes the wallpaper doesn't even load. If I switch to a tty (e.g. ctrl+alt+F1) and switch back, everything is just black except the mouse pointer. Top tells me that things are still running (even Conky although if it loads, it doesn't appear to refresh on the screen). It seems like the screen just stops updating altogether (except for the mouse pointer) somewhere in the middle of the Gnome startup process.

I've tried logging in with the "Netbook Edition" session selected, and the same thing happens. I've even tried running 'startx' as root to start with a fresh Gnome environment, and the same thing happens.

I've tried renaming my .gnome2 and .gconf directories to start with a fresh environment, but it still freezes after loading most or all of the startup programs.

I've tried renaming my xorg.conf, and I've tried switching between the "nvidia" and "nv" drivers, which also has no effect.

I've tried looking through logs but I'm not really sure which logs to search nor what to search for.

Any ideas will be much appreciated. Thanks!

---

