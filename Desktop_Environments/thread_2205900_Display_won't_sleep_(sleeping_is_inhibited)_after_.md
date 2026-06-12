---
title: "Display won't sleep (sleeping is inhibited) after VNC connection"
date: 2014-02-16
forum: Desktop Environments
---

### Post by quadra on 2014-02-16
I have a Xubuntu 12.04 workstation running vino-server 3.4.2 (for VNC access). 

In Power Manager (xfce4-power-manager), the physical monitor is set to sleep after 1 minute of inactivity.
This works well after reboot. However, after I first connect to the machine using VNC, and then disconnect again, the display will always remain on.
(Client used: TightVNC portable on Windows, built Oct 29 2009)

Looks like VNC somehow inhibits the xfce4 power manager.

As a **successful workaround**, I have created a task that will periodically restart the power manager.
(Using gnome-schedule, create a task that runs every hour. Configure it as "X application (suppress output)")

```
xfce4-power-manager --restart
```


Better solutions would be welcome. And, how can we find out if it's a problem in TightVNC, vino-server, or in xfce4-power-manager?

---

