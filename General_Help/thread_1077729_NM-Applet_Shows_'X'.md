---
title: "NM-Applet Shows 'X'"
date: 2009-02-22
forum: General Help
---

### Post by vahnx on 2009-02-22
I just set up a static IP address manually in [B]/etc/network/interfaces
[/B] and my net is working fine, just nm-applet is showing a little red x in the lower right-hand corner of the icon, and under information it says "No active connections found" and my connection doesn't show up under "Edit connections".

Here's the contents of /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.2
        netmask 255.255.255.0
        network 192.168.0.1
        broadcast 192.168.0.255
        gateway 192.168.0.1
```

---

### Post by Ubunt2u on 2010-01-28
I know this is an old post, but I'm having exact same issue after upgrading from 8.04 to 9.10.  Internet connectivity is working fine, but this is kind of annoying......

---

