---
title: "None of my internet connections are working on Linux!"
date: 2006-01-09
forum: General Help
---

### Post by Sopranosmainman on 2006-01-09
hey guys.... when i first started with linux it detected my internal wireless card and my ethernet port.... had no problems getting online..... Then i got greedy and wanted to work wireless with my Linksys WPC54GS card w/ Speedbooster.... so i installed NDISWRAPPER...downloaded the proper drivers.... and followed the directiosn to the T and guess what.... my Linksys card worked!.... so i disabled my internal wirelss card, shut down and went to bed. Then today i loaded up.... no internet ocnnection.... when i went into network settings.... i could not enable anything.... if i press enable... it would quickly disable... on all my NETWORK CONNECTIONS. Now i cant get on the internet for nothing. Can anyone hlep me get any of them working! Thanks in advance!

---

### Post by wanger123 on 2006-01-10
Hi, can we see your /etc/network/interfaces and /etc/resolv.conf files please?

Also, do you mean that neither your ethernet nor wireless cards work?

wanger

---

### Post by Sopranosmainman on 2006-01-10
well thankfully i got my wireless cards to work again, after much agony... but i still cant get my ethernet connection to work... it is detected... but when enabled it just quickly disables itself.

---

### Post by wanger123 on 2006-01-12
Still waiting for those files. 

wanger

---

### Post by Sopranosmainman on 2006-01-12
[Sorry... but i have been so busy with work and the gym i havent had time to get back on here.... here is the interfaces and resolve.conf

B]Interfaces[/B]

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
iface eth0 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid J-Network RE
	wireless-key1 xxxxxxxxxx
	wireless-key xxxxxxxxxx


iface wlan0 inet dhcp
wireless-essid any
wireless-key **********

iface eth1 inet static
netmask 255.255.255.0

auto eth0

[B]
Resolve.conf[/B]
nameserver 167.206.245.73
nameserver 167.206.245.72
nameserver 167.206.245.9

Again its just my ethernet LAN connection that doesnt work now. Thanks

---

### Post by wanger123 on 2006-01-13
Hi Sopranosmainman, I dont know whether this will fix it or not, but whenever I stuff up my connections I always get 2 new entries in the interfaces file that I need to remove and also re-enter my gateway (which you wont need as you are dhcp not static). The 2 entries are:

address 127.0.0.1
netmask 255.0.0.0

and then I save the file and do an ifconfig eth0 (or whatever yours is), then ifup eth0 (or whatever yours is) or sometimes I need to restart

hope it works (dont forget to backup the file first)

[EDIT] Come to think of it, could you just tell us what each interface is, ie eth0=wireless?, eth1=ethernet?? etc. Because I notice that eth1 is static but there are no properties such as DNS servers, broadcast, gateway, network, IP address etc

wanger

---

