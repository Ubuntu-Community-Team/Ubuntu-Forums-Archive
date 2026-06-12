---
title: "Wifi refuses to Connect, i think it hates me"
date: 2006-02-07
forum: Desktop Environments
---

### Post by shade11 on 2006-02-07
THIS IS A MAJOR PROBLEM. I REALLY NEED THIS FIXED!!!

I have been having troubles with my wifi connection. every time I login I will either not connect to my network or DHCP fails. I know it is not initNG becuase I did a normal boot and it still failed.

I tried using Wifiradar but it didnt work. The default network manager doesn't work either. And gtkwifi refuses to work.

I managed to write a shell script in /usr/local/bin that works but it only works for one Wifi connetion.

```
#/bin/bash
ifdown eth1
iwconfig eth1 essid WheaW
iwconfig eth1 key <censored>
ifup eth1
```

If someone can please tell me what to do.:confused: 

If I can't get this fixed I may have to put Windows XP back on and I don't want to do such a thing.

---

### Post by Mikecore on 2006-02-07
Well before you Put Xp back on your laptop maybe you should post your wifi nic spec's the driver your using and the failure message. So someone can try to help you.

---

### Post by adi-beg on 2006-02-08
What is your /etc/network/interfaces?

---

### Post by shade11 on 2006-02-08
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
	map eth1

# The primary network interface
iface eth1 inet dhcp
	# wireless-* options are implemented by the wireless-tools package
	wireless-mode managed
	wireless-essid WheaPavillion
	wireless-key <censored>

auto eth1

iface eth0 inet dhcp





auto eth0
```

Whaaaa. . . WheaPavillion, I dont connect there often. There shouldn't be a default anyway except maybe one called wireless.

eth1 is mt WLAN and eth1 is default.

---

### Post by shade11 on 2006-02-08
Please Help!

---

### Post by Ramses de Norre on 2006-02-08
Mine is a bit larger: ```
# The primary network interface
iface ath0 inet static
address 192.168.123.106
netmask 255.255.255.0
gateway 192.168.123.254
wireless-essid RAFAEL
wireless-key "xxxxxxxxx"

auto ath0

```
But that's probably be because I don't use DHCP, maybe you could try filling in all the details and turn off DHCP? DHCP just didn't work fine for me.

---

### Post by shade11 on 2006-02-08
But I need DHCP. Without it I can't connect to the internet.

PLEASE HELP ME!

---

