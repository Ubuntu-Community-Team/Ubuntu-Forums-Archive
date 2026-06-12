---
title: "Connected to wireless router, not getting packets"
date: 2006-01-15
forum: General Help
---

### Post by MarkBaum on 2006-01-15
I have a dlink 520 E1, and after going through the process of getting it installed

[https://wiki.ubuntu.com/DLinkDWL520E1](https://wiki.ubuntu.com/DLinkDWL520E1)

I can now connect to routers in the area.  The problem is that I cannot, for whatever reason, get on the internet with it, or even connect to the routers admin page itself.  There are some weird things I don't understand, for instance in the graphical networking utility it shows up as disabled sometimes, at the same time I'm connected to the router according to both the routers status log and the wifimanager.  I have been able to scan all of once, and even when I could scan I couldn't get on the internet.  Most of the time I can't scan at all.  

I don't know if this is worth anything, but there is another network called wifi0 that I can't figure out how it's still listed in the graphical utility, and keeps popping back up in /etc/network/interfaces even after I remove it and restart.

There are a ton of posts about problems with this card, but I havn't found any that relate to it working, but seemingly not able to recive packets.


```


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

iface wlan0 inet dhcp
        hostname localhost
        fw_primary /etc/firmware/pm010102.hex
        fw_secondary /etc/firmware/rf010804.hex
        wireless_mode managed 
        wireless-key **********
        wireless-essid default




auto wlan0


auto eth0

```

I honestly don't know what to post in order to help figure this out, but I'm hoping it's just one of those little things, as I'm connected to the router at the least.

---

