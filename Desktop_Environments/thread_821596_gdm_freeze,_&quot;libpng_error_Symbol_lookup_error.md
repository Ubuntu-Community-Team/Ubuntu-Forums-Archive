---
title: "gdm freeze, &quot;libpng error: Symbol lookup error&quot; -- What's this?"
date: 2008-06-07
forum: Desktop Environments
---

### Post by oleksus on 2008-06-07
I'm using Feisty on a Toshiba laptop.

Everything was running smooth.

I needed libart2-0 for some app, so I downloaded it, installed dependencies (like libatk, libglib) and then the GNOME suddenly seemed to freeze and reported something like 'broken cache' or something.

I reboot, and gdm freezes just before login screen.
I go to terminal, update gdm, reconfigure it, and it says:

```

gtk-update-icon-cache: symbol lookup error: /usr/local/lib/libpng12.so.0: undefined symbol: _InflateInit

``` 

I downloaded and installed what seemed the latest libpng, but gdm keeps freezing on startup and saying me this.

Is there a flaw somewhere, or have I accidentally screwed more libraries than I see?

---

### Post by Odrodzona-Sarmacja on 2008-07-07
Did you try downgrading libpng to an earlier version? Usually I get downgraded packages from "http://packages.ubuntu.com/".

Did you try downgrading libsdl packages?

Did you try installing more various libsdl packages to cover other sound&graphic settings?

Did you check libart2-0 dependencies?

Also I am experiencing these freezes, when networking. However uninstalling network-manager and working offline fixed my problems with these freezes. [http://ubuntuforums.org/showthread.php?t=840686](http://ubuntuforums.org/showthread.php?t=840686)

---

