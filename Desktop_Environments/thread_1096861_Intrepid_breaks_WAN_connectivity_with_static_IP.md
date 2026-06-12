---
title: "Intrepid breaks WAN connectivity with static IP"
date: 2009-03-15
forum: Desktop Environments
---

### Post by fade2gray on 2009-03-15
Testing on VirtualBox.

I have perfect LAN **and** WAN connectivity on Intrepid **Server** using 

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
	address 192.168.1.100
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
```

With Intrepid **Desktop** (Ubuntu and Xubuntu), I have LAN but **no** WAN

I had no such problem with Hardy Server/Desktop.

Is this a bug with Intrepid Desktop, or am I missing something?

---

