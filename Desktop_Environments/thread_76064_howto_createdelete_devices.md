---
title: "howto create/delete devices?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by ivago on 2005-10-14
Hi all,

just installed Breezy as a test and as a diehard Fedora user I must  admit that they did a really nice job.

But I have only 1 problem.

I have this wifi card wich is not supported with the prism54 driver
```

0000:02:00.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Pri sm Xbow] (rev 01)
```

this is my dmesg|tail output
```

[4297497.798000] prism54: request_firmware() failed for 'isl3886'
[4297497.798000] eth0: could not upload firmware ('isl3886')
[4297497.798000] eth0: islpci_reset: failure
[4297523.833000] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[4297534.248000] eth1: no IPv6 routers present
[4300828.914000] eth0: resetting device...
[4300828.914000] eth0: uploading firmware...
[4300829.020000] prism54: request_firmware() failed for 'isl3886'
[4300829.020000] eth0: could not upload firmware ('isl3886')
[4300829.020000] eth0: islpci_reset: failure

```

this is no problem, just install ndiswrapper and load the wintendo driver wich also works with ndiswrapper in my Fedora setup (dualboot pc)

```

gb@TACO:~$ ndiswrapper -l
Installed ndis drivers:
prisma00        driver present, hardware present

```

All I had todo in Fedora now is put 'alias wlan0 ndiswrapper' in /etc/modprobe.conf. 
-In Breezy ndiswrapper -m placed the wlan0 module  in /etc/modprobe.d/ndiswrapper.

I load the module with ```
modprobe ndiswrapper
``` 
and with Fedora I created a new network device wlan0 trough Fedora's networkmanagement **and this is where my problem starts**


Breezy created an eth0 device during install for the prism54 module but in network-admin or /dev/* it can't find any wlan0 devices. Furthermore it's not possible with network-admin to create or delete network devices, just to edit the IP and such?

So here's my question, how does one create a new wlan0 network device in Breezy and delete the eth0 network device, I also want to make sure Breezy doesn't load the prism54 driver anymore at boot.

I searched in /etc/modules and /etc/modprobe.d/* and /etc/network/interfaces and I've been searchin' this forum but I can't find the equivalent for Red Hat's /etc/modprobe.conf

Can somebody help me out here? How can I get this wlan0 device up and runnin' ?

All pointers are welcome and If you need more I'll provide it with pleassure :)

thx!

Ivago

---

### Post by ivago on 2005-10-14
yiiihaa got t solved.

problem was that during boot the prism54 module got loaded and binded to the hardware, leaving ndiswrapper without any hardware left tobind.

So i just added prism54 to /etc/hotplug/blacklist to prevent prism54 from loading during startup. After reboot wlan0 got created automagically., and after some tweaking I even got my wpa working again

hope this info will be helpful for somebody else.

ivago

---

### Post by banzoo on 2005-11-07
Hi,
I would like if u explain again in a step by step way how did u manage to enable the wifi, i do have same card as u on the laptop, i did install the windows driver wiz the ndiswrapper, added prism to blacklist, modprobe the ndiswrapper.
After rebooting, i cannot find eth0(the one associated to the wifi card once on prism driver) nor the wlan0
have i made anything wrong.
btw i'm using the amd64 ubuntu if that's can coz any problem
Thanx

---

### Post by ivago on 2005-11-15
I've saw something 'bout problem when mixing wn32 driver *.inf files in ndiswrapper running on 64 bit distro's. Unfortunately I'm still having i386 hardware so I can't help you out more, but there's definitely a better explanation on this forum or the ndiswrapper wiki.

good luck!

---

