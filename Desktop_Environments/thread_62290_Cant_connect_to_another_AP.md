---
title: "Cant connect to another AP"
date: 2005-09-04
forum: Desktop Environments
---

### Post by alvonsius on 2005-09-04
Hello everyone,

I'm currently using Compaq M2232 (ipw2200) to connect to my office wireless (Yes, i've already update the driver). It goes OK with essid and key of my office. But when i goes to another place, and use that place essid and key I can't connect to it using DHCLIENT. FYI, that 'anoter place' is using DHCP and my office is using Static Address. My question is, is this problem caused because of my /etc/network/interfaces/ is wrong? I'm currently using my office static address written on that file. Or there is another way to set this up? I've trying the dhclient and it just goes querying for 7 times with no result. The AP is detected (I try the K Wifi Assistant tool too) but ... Or there is another 'I dont know' settings???

Gosh ... I still struggle with this problem. Hope anyone can help me ... any hint is very valuable ... Thanks guys ...

This is my interfaces setting

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
#auto eth0
#auto eth1
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
# script grep
# map eth1

# The primary network interface
iface eth0 inet static
 address 192.168.1.27
 netmask 255.255.255.0
 network 192.168.1.0
 broadcast 192.168.1.255
 # dns-* options are implemented by the resolvconf package, if installed
 dns-nameservers 192.168.1.250
 gateway 192.168.1.250

iface eth1 inet static
 address 192.168.1.187
 netmask 255.255.255.0


PS: to connect from my office I'm using iwconfig and route command line

---

### Post by daller on 2005-09-04
Please add this to your sources.list:

#Office

iface office inet dhcp
wireless-essid OFFICE-ESSID
wireless-key OFFICE-KEY

#---

then use "ifup eth1=office" to up that interface!

Does that work?

---

### Post by mlomker on 2005-09-04
Switching between dhcp and static is a pain on linux.  Take a look at this [howto.](http://arstechnica.com/columns/linux/linux-20040413.ars/2)   I am using wpa_supplicant and ifplugd and it's a real help.  I didn't have any luck with guessnet, but perhaps that's unique to my wireless card and/or AMD64...not sure.

---

### Post by alvonsius on 2005-09-04
Thanks guys ... I'll give it a try and I'll report it to you all soon.

---

### Post by alvonsius on 2005-09-05
[QUOTE=alvonsius]Thanks guys ... I'll give it a try and I'll report it to you all soon.[/QUOTE]
 Humm ... it doesnt work. After a few check, I found out that the Address of Access Point is not changing. Is it normal? Or everytime i connect to different ESSID the AP should change into another address???

I'm using iwconfig to check the AP and nothing changes, but the ESSID is changes ...

Any hints?

Thanks guys ...

---

### Post by alvonsius on 2005-09-05
[QUOTE=alvonsius]Humm ... it doesnt work. After a few check, I found out that the Address of Access Point is not changing. Is it normal? Or everytime i connect to different ESSID the AP should change into another address???

I'm using iwconfig to check the AP and nothing changes, but the ESSID is changes ...

Any hints?

Thanks guys ...[/QUOTE]
 Sorry my fault ... the AP was correct.

Now I really confuse. I was thinking to give ndiswapper a try. Is there any issue about ndiswrapper? Or maybe there is some bad thing about it compared to the ipw22200 driver?

Oh yea, i think this is a driver problem, and i found a [patch](http://ieee80211.sourceforge.net/)  about ieee80211 1.0.3 and does anyone know how to use it?

---

