---
title: "Dell Inspiron - Wired and Wireless Simultaneously"
date: 2007-10-28
forum: Dell  Ubuntu Support
---

### Post by kidcharles on 2007-10-28
Hi all, I have an Inspiron 1505 that was preloaded with Fiesty. I'm trying to use both the wired and wireless network connections simultaneously. The wireless I want to connect to a router for internet access and the wired I want to use to connect to a computer that is not on the wireless network. It seems I can't get them both to work at the same time. If I configure the wired network the wireless stops working. There used to be a selection for default gateway too in the System->Administration->Network but that seems to be gone in Feisty, so there is no way in the GUI to say which connection is the internet connection. Anyone have any success with this? I've done something similar with my desktop PC, is there anything about Dell laptops that makes this impossible? Thanks.

---

### Post by dacap06 on 2007-10-29
Your desire is certainly possible in Linux.  I use the Kubuntu version instead of Ubuntu so I could be wrong, but I suspect the problem is that the Ubuntu Sysadmin GUI used to set up networking is too simple-minded for your scenario.  However, setting up your computer is easily done by editing files.  I haven't done this in Ubuntu, but I have done it in Red Hat and Mandriva.  This area is in the kernel and is common to all Linux distributions, so my experience applies.

Let's say that you access your wireless network using an atheros device ath0, and that you access your ethernet network with eth0.  Assume your wireless network is a class C private network with a network address of 192.168.1.0 (all 192.168.X.X networks are private), and your ethernet network is a class A network subnet with a network address of 10.1.2.0 (if memory serves, the 10.X.X.X network is private too).

Assigning IP addresses is easy enough, that can be done with the simple-minded GUI.  The problem is the entries in the kernel's routing table.  Say your default gateway is your WAP at IP address 192.168.1.1.   In that case, the response to the "route" command would look something like:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0    *               255.255.255.0      U     0      0        0 ath0
default         192.168.1.1         0.0.0.0         UG   0      0        0 ath0

You'll notice there's an entry for 192.168.1.0 (the wireless network) and a default route that points to the gateway.   But you need one more entry for your ethernet network!  Otherwise, all the packets that should be routed through the ethernet device are instead sent to the WAP via the default route. The way to handle that is to use your rc.local initialization script to create the missing routing table entry.  This script is used for local customizations specific to the machine.   Edit /etc/init.d/networking as root and add the following line in the START case:

route add -net 10.1.2.0    netmask   255.255.255.0   eth0

but substitute the appropriate network address, netmask, and device for your situation.  To make your script robust, you should make the route command conditional upon the presence of the network and that it is up.

Be sure to make a backup copy of rc.local before you modify it - you can easily screw things over and it's harder to recover without the original.

---

### Post by kidcharles on 2007-10-31
Thanks for the detailed response. I actually managed to get things to work simply by leaving the "Gateway Address" blank when manually configuring the wired network and set the wireless to "roaming" mode. I assume it then thought it must use the other active network, the wireless, as the gateway, and indeed it did, as I was able to access the internet wirelessly while accessing a separate PC through a crossover cable. I agree the Gnome Network Manager interface is too simplified. In Edgy you could choose which adapter was the default gateway but that mysteriously disappeared since Feisty.

---

