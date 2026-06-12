---
title: "WINE and screensaver crash Gnome"
date: 2011-01-22
forum: Desktop Environments
---

### Post by ZaphodFJ on 2011-01-22
Just did a rebuild of my PC (after a power-cut borked an upgrade from 10.04 to 10.10).

I...

-Installed 10.04
-Created /etc/X11/xorg.conf to get my monitor working with 1024x768 (previously, only 800x600 and 640x480 were picked up).  Everything appeared to work fine.
-Upgraded 10.04 to 10.10

And only after doing this, have I discovered that:

- Launching Wine crashes Gnome (I didn't try this under 10.04)
- The screensaver crashes Gnome (it was fine under 10.04)
- changing graphics display from 1024x768, at 70Hz crashes Gnome. (not attempted in 10.04)

In all cases, the 'crash' involves the display going weird - random sections appear enlarged, then Gnome restarts.

Any thoughts?

TIA.

---

### Post by ZaphodFJ on 2011-01-24
Not properly solved, but fixed by reinstalling 10.04.

Plenty of other, unsolved, posts about this one.  Seems to be an issue in 10.10 and/or Gnome that has been reported.

z

---

