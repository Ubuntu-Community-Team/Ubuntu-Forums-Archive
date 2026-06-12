---
title: "Wireless Connection Goes Up Only Few Minutes"
date: 2005-08-24
forum: Desktop Environments
---

### Post by alvonsius on 2005-08-24
Hi it's me again, after my last post (the one with error on boot -- 17 read no replies  \\:D/  ), i decided to re-install my kubuntu, and everything goes smooth ... but my wireless become weird ...

I'm using Compaq M2232 (intel ipw2200), and my wireless just go up for a few minutes and after that it goes down forever (at least until i reboot my machine). With the wireless applet running it shows an unstable connection, the bar goes up and down ... and after a few minutes it goes down. It is possible that the system turn the wi-fi off in case of unstability of my network? Any way I can turn this "kind-but-painless" feature?

This is my /etc/network/interfaces ... hope there is something wrong here 

```

## This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#       script grep
#       map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.1.187
        netmask 255.255.255.0
        network 192.168.1.0
        gateway 192.168.1.250
        broadcast 192.168.1.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.250

iface eth1 inet static
        address 192.168.1.187
        netmask 255.255.255.0
        gateway 192.168.1.250
        wireless-essid  "xx"    // sorry encrypted  ;-) 
        wireless-key    xxxxxx // sorry again  ;-) 


```

---

### Post by humanity_to_others on 2005-08-24
[http://ubuntuforums.org/showthread.php?t=26623](http://ubuntuforums.org/showthread.php?t=26623)

---

