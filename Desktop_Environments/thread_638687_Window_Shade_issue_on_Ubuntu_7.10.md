---
title: "Window Shade issue on Ubuntu 7.10"
date: 2007-12-12
forum: Desktop Environments
---

### Post by haydentech on 2007-12-12
I used to be able to roll up a window by doing a mouse-wheel-up in the title bar, and unshade it by doing a mouse-wheel-down in the title bar.  After a recent reboot, that doesn't work anymore.  I can still double-click to shade/unshade, but I much preferred the old mouse wheel behavior.  Where can I set this?  I am using compiz, if that matters.

---

### Post by haydentech on 2007-12-12
OK, responding to my own question here since I seem to have solved it...

Recently apt-get complained about a conflict with Emerald and suggested that I run a command to clean it up.  This had the effect of uninstalling Emerald.  It turns out that the scroll-wheel windowshade only works when Emerald is installed.  Oddly, however, I can't find any option in Emerald Theme Manager which actually turns this on/off.  It apparently just comes as an always-on feature of Emerald.

I didn't immediately make the correlation since I didn't log off or restart for several weeks after the Emerald uninstall, so Emerald was still in memory doing its thing.

---

