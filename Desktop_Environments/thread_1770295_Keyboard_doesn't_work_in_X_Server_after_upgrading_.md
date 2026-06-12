---
title: "Keyboard doesn't work in X Server after upgrading to 10.04"
date: 2011-05-29
forum: Desktop Environments
---

### Post by vvd416 on 2011-05-29
Upgrade to 10.04 - keyboard doesn't work in X Server
After I finished upgrading Xubuntu from 9.10 to 10.04, I discovered that my keyboard stopped working in X Server. The upgrade process was running smoothly until the last moment, when it produced some error, which I, unfortunately, did not write down.

Anyway, the upgrade has completed; uname shows kernel version 2.6.32-31. Now the keyboard works fine if I select a recovery mode at startup, but if I type 'start gdm' from the shell or select the default option in GRUB while booting, the keyboard becomes unavailable right from the login screen. I can log on using the virtual keyboard, but that's all I can do; the keyboard is still dead.

In the Xorg.0.log I found the following piece, which might be relevant to the case:

(II) LoadModule: "kbd"
(WW) Warning, couldn't open module kbd
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) No input driver matching `kbd'

My questions are:
- Is this issue known?
- If yes, then is there any way of enabling the keyboard in GUI without reinstalling the system?

---

