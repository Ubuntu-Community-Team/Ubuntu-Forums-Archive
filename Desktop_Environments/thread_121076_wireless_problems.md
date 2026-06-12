---
title: "wireless problems"
date: 2006-01-24
forum: Desktop Environments
---

### Post by dodgeman79 on 2006-01-24
My wireless card works great if I manually start it up.  But I'm trying to edit the interfaces file to get it to start up during the boot sequence.    As it stands now the system will hang after I log in.  but if I comment out all the lines then the system logs in fine but no card starts up.  Here is the interface file.

```
  GNU nano 1.3.8         File: /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

#auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
   script grep
    map eth3

iface eth3 inet dhcp
wireless-mode managed
wireless-essid OE-111
wireless-key 1152744D0B

auto eth3

```

---

