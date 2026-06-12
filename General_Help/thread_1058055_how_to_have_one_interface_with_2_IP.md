---
title: "how to have one interface with 2 IP?"
date: 2009-02-02
forum: General Help
---

### Post by markp1989 on 2009-02-02
I recently got a new router, and it gives out ip addresses differently . 

i have my server set to the new way that ips are given out, but some some devices are still looking for the old ip. 

so the question is , how do i set up 2 static IP addresses on the same machine , but only 1 NIC? 


thanks markp1989

---

### Post by ian dobson on 2009-02-02
Hi,

Here's my /etc/network/interfaces file, eth1 has 2 ip addresses 192.168.0.1 and .2

```

# The loopback network interface
auto lo eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.254

auto eth1:0
iface eth1:0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255

```

note the auto eth1:0 for the second ip configuration.

Regards
Ian Dobson

---

### Post by markp1989 on 2009-02-02
> **ian dobson said:**
> Hi,

Here's my /etc/network/interfaces file, eth1 has 2 ip addresses 192.168.0.1 and .2

```

# The loopback network interface
auto lo eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0
broadcast 192.168.0.255
gateway 192.168.0.254

auto eth1:0
iface eth1:0 inet static
address 192.168.0.2
netmask 255.255.255.0
broadcast 192.168.0.255

```

note the auto eth1:0 for the second ip configuration.

Regards
Ian Dobson

thankyou for speedy response, worked perfectly:D

---

