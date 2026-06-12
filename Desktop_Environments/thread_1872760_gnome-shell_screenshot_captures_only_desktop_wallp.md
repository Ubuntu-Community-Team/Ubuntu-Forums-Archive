---
title: "gnome-shell screenshot captures only desktop wallpaper"
date: 2011-10-31
forum: Desktop Environments
---

### Post by Schr on 2011-10-31
Hi,

When trying to screenshot of either a window or the whole screen, all I get is the wallpaper (or parts of it). The are from which the the screenshot is taken is correct, but the screenshot ignores all windows.

When I press the PrintScreen button it "flashes" the wallpaper over all my running apps, then takes the picture.

This happens even when running gnome-screenshot from command line, but I also get an error

```

** (gnome-screenshot:15121): DEBUG: The GetProfileForWindow request failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ColorManager was not provided by any .service files

```

---

### Post by Beryllium on 2011-11-22
Exactly what is described happens to me too.

---

### Post by Frogs Hair on 2011-11-22
Enable the Alt + F2 command prompt from Keyboard Settings > Shortcuts > System . Run the following command and try print screen again .```
r
``` OR ```
reset
```

Gnome Cheat sheet : [http://live.gnome.org/GnomeShell/CheatSheet](http://live.gnome.org/GnomeShell/CheatSheet)

---

### Post by yaddoshi on 2011-12-15
Restarting gnome-shell didn't work for me.

If it helps, I only noticed this issue after I switched from open source drivers to AMD Catalyst 11.12 for my Radeon 5850 - it's not an issue when I'm in Gnome Classic (no effects) however.

---

### Post by Beryllium on 2011-12-20
Again, this happens to me too. Restarting gnome shell doesn't help, the background still flashes up. I'm using a Radeon 54xx on the 11.11 drivers. I'll assume this is an issue with fglrx, which doesn't seem to play nice with the compositer.

---

