---
title: "Long wait for Gnome Splash Screen to go away...."
date: 2007-01-21
forum: Desktop Environments
---

### Post by encompass on 2007-01-21
It seems that when I log in the splash screen has to wait for a long time, around a minute, before it can continue to load.
For the time being I have disabled the splash screen.
It happens in both beryl and metacity, and it has happened ever since I first installed.
It there a way to check the logs of what program is stopping everything else to load.
I didn't have to worry about this before, but now with me using network manager it sucks to have to wait for it to load just to use my wireless connections.
BTW the system doesn't use any processor power while waiting for the application.  It seems as though it is just timing out.
Thanks for the help everyone.

---

### Post by dcstar on 2007-01-21
> **encompass said:**
> It seems that when I log in the splash screen has to wait for a long time, around a minute, before it can continue to load.
For the time being I have disabled the splash screen.
It happens in both beryl and metacity, and it has happened ever since I first installed.
It there a way to check the logs of what program is stopping everything else to load.
I didn't have to worry about this before, but now with me using network manager it sucks to have to wait for it to load just to use my wireless connections.
BTW the system doesn't use any processor power while waiting for the application.  It seems as though it is just timing out.
Thanks for the help everyone.

You may want to remove the "quiet" option from your Grub boot list, and enable the BOOTLOG option (in /etc/default, I think).

You might then see what is delaying your boot-up, it is probably something timing out due to a mis-configuration somewhere.

---

### Post by encompass on 2007-01-22
so I think it has to do with d-bus because all the programs that load after the delay use dbus.

---

