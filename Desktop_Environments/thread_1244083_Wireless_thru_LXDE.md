---
title: "Wireless thru LXDE"
date: 2009-08-19
forum: Desktop Environments
---

### Post by isee on 2009-08-19
Are LXDE questions allowed?

I can't seem to find how to activate a wireless connection in LXDE desktop.  I've tried LXDE forum but there has been no response.

I can plug in through a LAN cable to my router, but I must say even with that, to go offline I have to unplug the cable, as there seems to be no "disconnect network" option.

---

### Post by mcduck on 2009-08-19
If you want, you could just use the same Network Manager that Gnome uses for this.

Assuming you have it already installed, simply run "nm-applet" to start it. Then add that command your startup applications (I can't remember how that's done in LXDE).

---

### Post by isee on 2009-08-19
This response thru Terminal in LXDE
~ @ -laptop:~$ nm-applet
** (nm-applet:3432): DEBUG: applet_common_device_state_changed
** (nm-applet:3432): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3432): DEBUG: applet_common_device_state_changed
** (nm-applet:3432): DEBUG: old state indicates that this was not a disconnect 0

This response thru Terminal in GNOME Edubuntu
** (nm-applet:4382): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3

I need a wireless hookup in LXDE environment.

Thanks!

---

### Post by XubuRoxMySox on 2009-08-19
Most people with LXDE **use wicd instead** of the Gnome network manager and it works with no problem.

For some reason installing LXDE disables the Gnome network manager. I think they're working on that li'l bug. But in the meantime just use wicd (which has no Gnome dependencies, by the way).

Install it from Synaptic.

-Robin

---

### Post by isee on 2009-08-19
Ahh...I made it!  Thanks very much Robin dixiedancer!  I had to navigate my way to allow encryption, but I figured it out.  I think I like wicd better than Network Manager, seems to have more user functionality.

---

### Post by XubuRoxMySox on 2009-08-19
Yaaaaay! You have no idea how good it feels to a newbie like me to do some good around here! I'm so glad I could help!

-Robin

---

