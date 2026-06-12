---
title: "eth0 from DHCP to static"
date: 2005-12-20
forum: General Help
---

### Post by stoeptegel on 2005-12-20
Hi,

My repaired motherbord came back today, and in the mean while i converted my router from DHCP to static. On windows i know how to convert and set this, but i kubuntu i am lost.
Can someone please give me some hints?

Thanks.

---

### Post by MartinG on 2005-12-20
I THINK what you're after is System Settings. Then Network Settings->Administrator mode.

Configure the interface to your chosen IP address and network mask, and set the default gateway on the routes tab to your router's (network) address.

You may have to set DNS server addresses also.

---

### Post by rattking on 2005-12-20
Hi
the kde way to do this is in 
Kmenu / System settings / Network Settings
go into administrator mode and configure your network interface to automatic dhcp

the cli way to do this is
sudo vi /etc/network/interfaces
change 
iface eth0 inet static
to
iface eth0 inet dhcp
comment out the address netmask and gateway lines
then restart your networking
sudo /etc/init.d/networking restart

hope this helps

---

### Post by stoeptegel on 2005-12-20
No the other way around, converting eth0 from DHCP to static. 


I've done the Network Settings in kde now, but when i do $sudo ifup eth0 i get:
```

/etc/network/interfaces:21: too few parameters for iface line ifup: couldn't read interfaces file "/etc/network/interfaces"

```


My config file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
address 192.168.1.34
netmask 255.255.255.0

iface eth1 inet 

auto eth0

```


And when i do $sudo /etc/init.d/networking restart:
```

* configuring network interfaces...                               [[COLOR="Red"]fail[/COLOR]]

```

---

### Post by spence on 2005-12-20
I use a static IP address and this is the important part of my /etc/network/interfaces file for comparison

auto eth0
iface eth0 inet static
address 132.aaa.bbb.ccc
netmask 255.255.255.0
broadcast 132.aaa.bbb.255
gateway 132.aaa.bbb.1

I hope that helps.
Spence

---

### Post by rattking on 2005-12-20
whoops read that wrong..
iface eth1 inet 
is incomplete.. it needs to look more like the eth0 line
iface eth1 inet static or dhcp

also eth0 may need an gateway if you have a router

here is mine




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
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        gateway 192.168.1.1


```

---

### Post by rattking on 2005-12-20
whoops read that wrong..
iface eth1 inet 
is incomplete.. it needs to look more like the eth0 line
iface eth1 inet static or dhcp

also eth0 may need an gateway if you have a router

here is mine




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
#iface eth0 inet dhcp
iface eth0 inet static
        address 192.168.1.100
        netmask 255.255.255.0
        gateway 192.168.1.1


```

---

### Post by stoeptegel on 2005-12-20
Thanks guys, it was that eth1 line, i removed it and now it's working. :)

BIG t-h-a-n-k-s!

---

