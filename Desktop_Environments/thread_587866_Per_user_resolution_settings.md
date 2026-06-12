---
title: "Per user resolution settings?"
date: 2007-10-23
forum: Desktop Environments
---

### Post by pantulis on 2007-10-23
Hi, 

Whenever I log in into my main user account, my monitor (Dell 1905) displays an Invalid Signal box.  After that, I ran dpkg-reconfigure xserver and the videocard (Intel 965) and monitor seem to be properly detected, with correct vertical and horizontal freq values.

Still, whenever I login the monitor won't do anything but complain of an improper signal.

But what is truly puzzling me is that after creating a fresh new user, one can log in with no problems -I see nice Beryl effects and all.  This implies that /etc/X11/xorg.conf is properly configured.  Also, selecting "Failsafe Gnome" on Gdm allows me to log in with the old account.

My guess is that there must be some per-user configuration that I am not aware of.    Any hints?

---

