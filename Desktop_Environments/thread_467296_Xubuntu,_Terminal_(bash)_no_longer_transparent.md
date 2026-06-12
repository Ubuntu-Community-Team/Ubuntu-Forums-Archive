---
title: "Xubuntu, Terminal (bash) no longer transparent"
date: 2007-06-07
forum: Desktop Environments
---

### Post by kevinfishburne on 2007-06-07
I'm running Xubuntu 7.04 with fglrx that I installed using Envy. I had bash set to be partially transparent and I believe it was that way even after installing the ATI drivers. My desktop is 3200x1600 across two monitors using ATI's "big desktop" or "horizontal" mode. Bash now has a solid background, even though in its options it's still set to be partially transparent. Any ideas why this is? I'm not running Beryl, Compiz, XGL, or anything weird like that.

Kevin

---

### Post by kevinfishburne on 2007-06-07
Resolved:

Strangely under *Desktop Settings*, *Allow Xfce to manage the desktop* was no longer checked, which was causing the problem. Several times I checked it and clicked *Quit* but the setting didn't take until I rebooted and tried it again. There seems to be a bug when toggling this option on and off any applying the settings between toggles. Sometimes the setting change takes, other times it doesn't. One time it seemed to half-way take, as I could right-click the desktop (which does nothing when the setting is toggled off) and create a folder, but the folder was not there when I looked for it in bash. It shouldn't have done anything when I right-clicked the desktop. Weird.

Kevin

---

