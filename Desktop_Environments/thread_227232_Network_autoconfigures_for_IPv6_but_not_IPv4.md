---
title: "Network autoconfigures for IPv6 but not IPv4"
date: 2006-08-01
forum: Desktop Environments
---

### Post by Eoin on 2006-08-01
During boot up Ubuntu does not seem to be configuring my network interface for IPv4 and does not get any details off of my dhcp server. I can solve this problem manually either by running ```
dhclient eth0
``` or by going into the System > Administration > Networking control and clicking to Deactivate and then Activate the eth0 interface.

Is there a way to make this automatic? My /etc/network/interfaces file is untouched since installation:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
```
Kind regards, Eoin.

---

### Post by Eoin on 2006-08-01
I sorted this myself. I removed all but the lo interface from /etc/network/interfaces and then I installed network-manager and everything is perfect :) .

---

### Post by newbieal on 2007-08-19
Hi,

I am having the same problem with my system. Could you please outline all the steps you took to get IPv4 recognized. I've installed the network manager (i think), but IPv4 still isn't being recognized.

Thanks,
Newbieal

---

