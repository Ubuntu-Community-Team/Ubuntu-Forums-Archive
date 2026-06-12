---
title: "boot hangs on network part of bootprocess"
date: 2006-01-05
forum: General Help
---

### Post by maol62 on 2006-01-05
I have an old computer that I want to connect to my second network card in my ubuntu machine. The second network card is integrated with the motherboard so therefore I enabled it in BIOS and then started up as normal with Ubuntu. Then I installed dhcp3-server via synaptics. Everything ok so far. But then I changed my mind and desided connect my old computer to the router instead of to the secondary network card. So I did a complete removal of dhcp3-server via synaptics and restarted computer, disabled the same network card as I enabled in the beginning.
And now, when I boot, the bootprocess hangs at Configuring network interfaces and Waiting for network interfaces to come up. Booth theese steps I have to press ctrl-C to get through. Does anyone know what could be wrong?

---

### Post by alamba on 2006-01-05
Did you disable it from BIOS too? Does it still show under system>admin>networking?

Akshay

---

### Post by maol62 on 2006-01-05
Yes, it is disabled in BIOS too and it does not show up under system>admin>networking. There I can only see eth0 and the ppp0 (which is not used). The second network card was named eth1 when it was enabled in bios.

---

### Post by alamba on 2006-01-05
And is the first interface connected to the router with an IP from a dhcp source? The reason its waiting is because its trying to get you an IP.

Akshay

---

### Post by maol62 on 2006-01-05
The first interface is connected to the router and getting an ip-address from threre. The problem is that I think that some configuration file still has the eth1 interface within it and that the bootprocess is trying to set an ip-address to that interface too. But because of my removal of eth1 it is not possible and therefore it hangs. Before I messed it up by enabling it there was no problems with the boot. And I still get an ip-adress for my eth0, although I press ctrl-c to get on with the boot.

---

### Post by carlosqueso on 2006-01-05
does it show them in your /etc/network/interfaces file?  Post that file here if you wouldn't mind.

---

### Post by maol62 on 2006-01-06
Here is my /etc/network/interfaces file:

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
iface eth0 inet dhcp

auto eth0
```

---

### Post by alamba on 2006-01-07
nope...no eth1 here...did you get this resolved? do you have a toggle hardware switch by any change for your wireless card?

Akshay

---

