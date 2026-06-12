---
title: "VNC gets File Manager only"
date: 2017-01-22
forum: Desktop Environments
---

### Post by Geoff_Lane on 2017-01-22
Folks, I manage a Raspberry Pi running Ubuntu Mate remotely using my Ubuntu laptop.

Mainly use SSH and previously on occasions VNC via an SSH tunnel.

For some reason I started to get a grey screen, following a few online suggestions it now logs in but I get just a File Manager, no desktop.

The desktop on the actual Pi is working fine and  auto logs in to main user if rebooted.

I was using tightvncserver on Pi and remmina  on Laptop to access.

Any suggestions appreciated.

Geffers

---

### Post by TheFu on 2017-01-22
What does the xstartup for VNC contain?  That is likely the issue.
 [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

---

### Post by Geoff_Lane on 2017-01-22
> **TheFu said:**
> What does the xstartup for VNC contain?  That is likely the issue.
 [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-vnc-on-ubuntu-16-04)

```
#!/bin/sh

def
export XKL_XMODMAP_DISABLE=1
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
 
gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-terminal &



```

Geffers

---

