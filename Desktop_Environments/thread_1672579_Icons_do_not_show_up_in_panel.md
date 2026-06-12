---
title: "Icons do not show up in panel"
date: 2011-01-21
forum: Desktop Environments
---

### Post by math1985 on 2011-01-21
The following icons do not show up in my Gnome (2.32) panel, Ubuntu 10.10:
- Power management
- Wifi
- Keyboard layout
- Bluetooth

My network connection is also not working until I run nm-applet manually (then the wifi icon shows up too).

I tried already adding the notification area to the panel, but this does not help.

Under Startup Applications, amongst other the following applications are enabled: bluetooth-applet, nm-applet --sm-disable and gnome-power-manager. 

For other users, it works fine (also for a freshly created account).

Thanks in advance for any suggestions.

---

### Post by math1985 on 2011-02-04
This problem still exists.

When I start nm-applet manually, I get the following messages:

** Message: applet now removed from the notification area
** Message: applet now embedded in the notification area
** (nm-applet:1802): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1802): DEBUG: foo_client_state_changed_cb

Does this help? How can an applet be removed from the notification area if I don't see it there?

---

