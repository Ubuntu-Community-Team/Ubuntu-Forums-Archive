---
title: "Faster Static IP startup in 9.04"
date: 2009-05-16
forum: General Help
---

### Post by dcstar on 2009-05-16
After seeing log entries where networking had obviously not started before some processes attempted to use it in a standard 9.04 Desktop installation, there is a simple way to fix this and reduce the boot time of your system:

Simply add back in the (old) **gnome-network-admin** package and remove the (new) **network-manager** packages.

You can then use System-Administration-Network to set up your Static IP info and this actually places the data in the /etc/network/interfaces file (which Network Manager does not).

Unless you need the fancy stuff in Network Manager, all it seems to do is slow down the booting of your 9.04 system.

I would imagine that this also works in DHCP systems, but I haven't tested it myself.

---

