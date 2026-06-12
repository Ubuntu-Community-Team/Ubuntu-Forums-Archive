---
title: "network card not initialising"
date: 2006-09-21
forum: Desktop Environments
---

### Post by jamespi on 2006-09-21
i have a PCI ethernet NIC and a PCI wireless card. i have a USB ADSL modem, and i share the net connection over the wireless card.

for some reason, on every other boot the PCI NIC wont initialise. this results in my wifi card getting assigned eth1 instead of eth2 which then means my wifi card gets assigned all of the PCI NICs IP config, thus breaking my NAT.

here is my /etc/network/interfaces

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet static
	
	address 192.168.1.1
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	# gateway 192.168.0.1
	# # dns-* options are implemented by the resolvconf package, if installed
	# dns-nameservers 192.168.0.1

iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

auto eth1

iface ppp0 inet ppp
provider ppp0



iface eth2 inet static
address 192.168.0.1
netmask 255.255.255.0
pre-up iwconfig eth2 mode ad-hoc

auto eth2

auto ppp0


i dont know what logs to look in to figure out why the PCI NIC doesnt initialise.

---

### Post by jamespi on 2006-09-21
hmm i havent actually looked through that config file properly for ages - i always wondered why i never got eth0 - it seems to have a redundant entry. this is probably left over from when i had 2 network cards in. maybe i should clear out the redundant crap in there.

---

### Post by jamespi on 2006-09-21
ok, i've changed it to this, making the wifi card eth0 so hopefully if the NIC doesnt initialise it won't make any difference. i'll just reboot and see what happens.

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# WiFi card
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
pre-up iwconfig eth0 mode ad-hoc

auto eth0


# PCI NIC (to XBox)
iface eth1 inet static
	
	address 192.168.1.1
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	# gateway 192.168.0.1
	# # dns-* options are implemented by the resolvconf package, if installed
	# dns-nameservers 192.168.0.1

auto eth1

iface ppp0 inet ppp
provider ppp0



auto ppp0


---

### Post by jamespi on 2006-09-21
ok i cant get the wifi card tagged as eth0, it has some config somewhere i assume that says its eth2 so i have to leave it at that.

where are the iwconfig settings kept?

i have got rid of that redundant eth0 stuff in etc/network/interfaces so maybe that will stop the PCI NIC failing to initialise in some cases but i'm just clutching at straws.

here is my etc/network/interfaces as it stands

>  
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.


# WiFi card
iface eth2 inet static
address 192.168.0.1
netmask 255.255.255.0
pre-up iwconfig eth2 mode ad-hoc
wireless-essid hal

auto eth2


# PCI NIC (to XBox)
iface eth1 inet static

	address 192.168.1.1
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255

auto eth1

# USB ADSL Modem
iface ppp0 inet ppp
provider ppp0




---

### Post by jamespi on 2006-09-21
also my ADSL modem randomly fails to connect on startup, and i would also like to know how to make firestarter be loaded automatically when i log in.

---

