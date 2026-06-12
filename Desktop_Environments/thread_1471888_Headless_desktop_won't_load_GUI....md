---
title: "Headless desktop won't load GUI..."
date: 2010-05-03
forum: Desktop Environments
---

### Post by michaelslarsen on 2010-05-03
I have an Dell 755, and I have installed Ubuntu 10.4 desktop on it, everything works fine.  I have it auto login, and run Azureus/Vuse at startup (so it can be a headless Bit Torrent server), it works perfectly.  As soon as I try to go headless (no keyboard/mouse/monitor) the machine boots fine (I can SSH / FreeNX to the machine) but none of the GUI/apps load.  What I think is happening is that when it boots without a monitor attached it does not load any of the X11 stuff.  I need it to.  It worked in Ubuntu 9.04 just fine, but now with 10.4 it is a no-go.  Does anyone know how to force the X11/GUI to load when there are no monitors/hardware attached?  This is the one thing standing in my was of getting Windows out of my house.

Any help would be greatly appreciated!

---

### Post by Revelator7MD on 2010-05-04
Take a look at [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting). In my case, I upgraded from  9.10 to 10.4 on a headless machine, but then VNC with GDM stopped working. Suspecting GDM  wasn't loading properly, I followed [https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting),  where I ran the command:

```
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf
```(in my case I have a Radeon card)
then rebooted. Worked! :grin:

---

