---
title: "Automatic configuration of static ip at startup"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Nasso on 2005-10-26
I got a pcmcia ethernet 100/10mbit network card which is my main network card.
When i start ubuntu the eth0 device aint configured with the ip address i choose at the Network Settings-dialog.
To get it working i have to open the Network Settings-dialog, select eth0, click deactivate and then click activate.
Is there any way to automate this process?

---

### Post by tehwa on 2005-10-26
The configuration file that is edited by this networking dialog is located at:```
/etc/network/interfaces
``` It might be that something within this file is causing the issue. 

If you are unsure, post the contents here.

In terms of automating your process, It's difficult to automate modification to the state of network interfaces, since it's a root/sudo thing. However, you could probably bypass the networking GUI  and just type:
```
sudo ifdown eth0
sudo ifup eth0
```
into a terminal window until you get it sorted.

---

### Post by Nasso on 2005-10-26
k, thanks :)

here is my /etc/network/interfaces

I have a wireless card to, ra0. doesnt use it very often...
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.3
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

iface ra0 inet static
wireless-essid MG
address 192.168.1.127
netmask 255.255.255.0
gateway 192.168.1.1

auto ra0



---

