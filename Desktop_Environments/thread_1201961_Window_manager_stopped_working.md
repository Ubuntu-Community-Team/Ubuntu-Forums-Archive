---
title: "Window manager stopped working?"
date: 2009-07-01
forum: Desktop Environments
---

### Post by stewacide on 2009-07-01
When I rebooted my machine today (after not having done so in a couple weeks, with a bunch of updates installed in between) Gnome wouldn't launch: the panel came up for a second and then it dropped back to the login manager. At first I suspected a driver issue, so I messed around with that for a bit (trying different driver and kernel versions), but that didn't help. Then I tried uninstalling desktop effects, which allowed Gnome to start but but without a window manager (see attached screens). Any idea what went wrong / how to fix?

edit -- If I force Metacity to restart (with $metacity --replace or by trying to enable desktop effects with compiz not installed) the window decorations will come back, but if I then reinstall and try to enable Compiz I get booted back to login.

Ideas?

---

### Post by frt975 on 2009-08-03
I have this problem too.

---

### Post by frt975 on 2009-08-03
Goto System>Preferences>Startup Applications>Add
Choose any name you want, type "metacity" (without quotes) in the command text-box.

---

