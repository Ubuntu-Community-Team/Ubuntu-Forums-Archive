---
title: "[SOLVED] Reloading Xorg on system boot"
date: 2008-01-14
forum: Desktop Environments
---

### Post by ezramorris on 2008-01-14
Hi,
I'm not sure whether this is an issue with Xorg or not, but anyway...
A while back I installed Firestarter, set sudoers to allow running, and added it into startup --> Sessions.
However, when I rebooted, it did not start. I never really got round to sorting this.

Quite recently I was setting up LIRC, and got everthing working.  had to make a manual change to xorg.conf to enable mouse support. (mouse driver)

Anyway, the problem now is if I start Ubuntu, the xorg.conf new settings do not load. If, however, I press ctrl-alt-bksp, the mouse driver works, and Firestarter loads. So, how can I get this to be done on system boot?

Thanks.
--------------------------------
Ubuntu Gusty Gibbon 7.10

------------------------------------------------
[COLOR="Red"]Update: It appears as if Firestarter had loaded my settings, but just not put an icon in the system tray.[/COLOR]

---

