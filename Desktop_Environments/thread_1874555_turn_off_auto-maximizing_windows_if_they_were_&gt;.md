---
title: "turn off auto-maximizing windows if they were &gt; 70% when closed?"
date: 2011-11-03
forum: Desktop Environments
---

### Post by yarozar on 2011-11-03
How can I turn off that feature of compiz (?) that when you close a window that is sized more than 70% (not sure in that number) of screen then next time it opens maximized?

There is a bug with TwinView and two screens: when you resize app window in bigger screen to bigger sizes, then close it and reopen, it seems to compare that 70% not to total (or bigger screen) but to the small one (!) and thus all my apps now reopen maximized when I use two monitors. That's annoying.

Thanks!

P.S.: if someone know the right way to file bugs to Ubuntu and confirms my issue please file a bug to them; thanks!

---

### Post by drs305 on 2011-11-03
> **yarozar said:**
> How can I turn off that feature of compiz (?) that when you close a window that is sized more than 70% (not sure in that number) of screen then next time it opens maximized?

Take a look at the Unity Plugin in Compiz Config Settings Manager (sudo apt-get install compizconfig-settings-manager).

Desktop > Ubuntu Unity Plugin > Experimental. Set the Automaximize value to 100%.

---

### Post by yarozar on 2011-11-03
100% still counts against smaller screen. Is it possible to completely turn in off?

---

### Post by markbl on 2011-11-03
> **yarozar said:**
> 
P.S.: if someone know the right way to file bugs to Ubuntu and confirms my issue please file a bug to them; thanks!
There is a bug on this, or at least related. It looks like it will be fixed soon although it seems you are reporting a slightly different issue. See [https://bugs.launchpad.net/ayatana-design/+bug/797808](https://bugs.launchpad.net/ayatana-design/+bug/797808).

---

