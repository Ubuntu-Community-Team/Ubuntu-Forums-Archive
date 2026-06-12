---
title: "Static IP Adress - Diablo 2 Woes"
date: 2007-05-19
forum: Gaming &amp; Leisure
---

### Post by le_vainqueur on 2007-05-19
I've been playing Diablo 2 LOD in Ubuntu lately, and I was trying to set up a LAN game, but had no success.  One thing that isn't working correctly is that the game says that my IP address is 

127.0.1.1

I know that's another important number (although I don't quite understand what it means).  Here is my /etc/network/interfaces file

> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


iface eth0 inet static
address 192.168.1.136
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp


iface wlan0 inet dhcp


auto wlan0

auto eth0


Any tips?

---

