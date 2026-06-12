---
title: "loopback failed at boot"
date: 2006-01-30
forum: Desktop Environments
---

### Post by injectionpa on 2006-01-30
Short and sweet.  I have successfully created a nightmare. Three days ago after installing wpa_supplicant with a madwifi card on reboot the lo interface fails to load. 
I am using this on a laptop connected at home with wired/wireless at different times. I try to use a static address at home as I was having problems with dhcp and the wifi connection. 
[SIZE="4"][B]
??How to get the lo to start at boot again.??[/B][/SIZE] I did install ifplugd and have seen mixed comments about that. 



copy of interfaces 

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


# This primary network interface


# Wireless
allow-hotplug ath0
address 192.168.11.13
netmask 255.255.255.0
gateway 192.168.11.2

iface ath0 inet static
	address 192.168.11.13
	netmask 255.255.255.0
	gateway 192.168.11.2
	wireless-essid xxxxxxxxx


iface eth0 inet dhcp



auto eth0



thank anyone with any ideas?:evil:

---

