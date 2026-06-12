---
title: "Network-manager Ethernet constantly requesting dhcp"
date: 2007-07-25
forum: Desktop Environments
---

### Post by jcarlock on 2007-07-25
I have a Latitude d820 and all was well until I tried to swap (identical) machines to test beryl to ensure my issue was with beryl, not my hardware - Needless to say it is beryl.

But after doing that, I assume, it created a new interface called eth2, previously had eth0 (wired) and eth1 (wireless).  I assume it did this because of different MAC/ARP addresses, and I edited the /etc/network/interfaces file to only contain the interfaces it should after these issues started.  Now when the network-manager-gnome, (or knetworkmanager) tries to get a dhcp address, it does, but then it continues to request a dhcp address until it fails and claims it is disabled.  I know this because of the icon's roll over message.  If I remove the network manager packages, including configs, and reinstall, issue remains, also remained after trying knetworkmanager.

At this point I completely removed all instances of the network managers and just do the configuration (DHCP request) manually.  network-admin works fine still also, even without network-manager and network-manager-gnome.  I am certain that the issue is with the network manager trying to bind to a phantom mac address and not associating with the original.

Any clues would be much appreciated.

---

