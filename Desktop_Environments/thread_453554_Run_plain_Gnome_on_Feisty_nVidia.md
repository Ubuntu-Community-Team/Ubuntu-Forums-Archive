---
title: "Run plain Gnome on Feisty nVidia?"
date: 2007-05-24
forum: Desktop Environments
---

### Post by lramshaw on 2007-05-24
I'm running Feisty on a machine with an nVidia GeForce 3. When I enable the nVidia drivers and reboot, I get new, brighter themes and splashscreen, apparently because Ubuntu then runs compiz instead of gdm as its window manager?

Is there a way to switch back from compiz to gdm, while still using the accelerated drivers? Or, failing that, to make the old gdm themes and splashscreen available through compiz?

Thanks.

---

### Post by mgmiller on 2007-05-26
Ubuntu does not enable compiz by default.  Even if you install the accelerated drivers, compiz is not turned on unless you go to System>Preferences>Desktop Effects and turn it on.  If you did that and don't like what you see, go back there and turn it off.  That being said, as far as I know, the compiz effects don't kick in till your desktop appears, so the splash screen should not appear any different.  Themes, are another matter, windows will have drop shadows, and appear to "pop" a bit more, windows will wobble when you move them, etc. 

Normally, just enabling the accelerated drivers makes the whole system seem more responsive, drop downs and windows open faster and move easier.  Videos may play a little better and let you move and resize their windows with less problems.  But they don't normally look any brighter.

---

