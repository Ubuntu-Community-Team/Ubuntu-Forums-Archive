---
title: "kernel=3.5.0-22 -&gt; no cinnamon menu panel?"
date: 2013-01-20
forum: Desktop Environments
---

### Post by tlroche on 2013-01-20
Note that by "menu panel" I mean the panel that stretches the full width of the bottom edge of the Cinnamon Desktop, from which one accesses the main menu, program launcher, applet controls and indicators, etc. The problem is:

GF has a System76 Meerkat running ubuntu=12.10 with Nvidia graphics. She tried Unity and disliked it; I run LMDE with Cinnamon, so suggested that, and she likes and has been running that for a few months.

Today I ran `sudo aptitude update` and `sudo aptitude full-upgrade`, which upated the kernel (to 3.5.0-22) and a few other things (e.g., duplicity) but nothing major. For the kernel update I rebooted: ubuntu booted to the login (with no GRUB menu--more below), which worked, but after that, I got a black screen for ~10 sec, then ... just wallpaper, with no menu panel.

C-A-F1 works, so I fiddled with /etc/default/grub until I got the GRUB menu to show. I then booted to kernel=3.5.0-21 (the previous): after login, we et the black screen, then the full desktop (wallpaper with menu panel on lower border). Which was great! until I suspended the box. After waking, it put up the login dialog (which worked), then ... just the desktop, no menu panel.

I'd like to know, how to fix this (in the new kernel) or debug the problem? Failing that, is there somewhere I should report this?

---

### Post by tlroche on 2013-01-20
The one thing that works, so far, both before and after suspend, both with kernel=3.5.0-22 and previous, is the GNOME classic desktop. I.e., if I boot the default/newest kernel, and choose desktop="GNOME classic" @ login, I get wallpaper and both panels (top and bottom). I also get that after post-suspend login.

---

