---
title: "Vostro 1500 wireless quit working, what to do ???"
date: 2009-12-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by colinnwn on 2009-12-01
Hi,

Wireless on my Vostro 1500 quit working, I think after doing a normal Ubuntu system update. I dual-boot XP, and wireless works fine in XP. In the network manager applet, the "wireless enabled" menu item and checkbox is greyed out. This model has a switch to disable wireless (which I verified is in the on position), but no wireless Fn key as normal for Dells.

I tried following the [Wireless Troubleshooting Guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") relevant parts, though I skipped the parts clearly not relevant (such as restricted drivers, since I have an Intel wlan card). Here is the output of lshw and iwconfig-
```

colin@vostro1500:~$ lshw -C network

WARNING: you should run this program as super-user.

*-network DISABLED
	description: Wireless interface
	product: PRO/Wireless 3945ABG [Golan] Network Connection
	vendor: Intel Corporation
	physical id: 0
	bus info: pci@0000:0c:00.0
	logical name: wmaster0
	version: 02
	serial: xxxxxxxxxxxxxx
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master cap_list logical ethernet physical wireless
	configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
	resources: irq:28 memory:f9fff000-f9ffffff

*-network

	description: Ethernet interface
	product: BCM4401-B0 100Base-TX
	vendor: Broadcom Corporation
	physical id: 0
	bus info: pci@0000:03:00.0
	logical name: eth0
	version: 02
	serial: xxxxxxxxxxxxxxxxxx
	width: 32 bits
	clock: 33MHz
	capabilities: bus_master cap_list ethernet physical
	configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 multicast=yes
	resources: irq:17 memory:f9bfe000-f9bfffff


colin@vostro1500:~$ iwconfig

wlan0
IEEE 802.11abg  ESSID:""
Mode:Managed   Frequency:2.412 GHz   Access Point: Not-Associated   
Tx-Power=0 dBm   Retry long limit:7   RTS thr:off   Fragment thr:off   Power Management:off
Link Quality:0  Signal level:0  Noise level:0
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

Looks like the wlan card has been switched off, but clearly it hasn't, and I've tried everything I can think of (and google) to fix it. Can anyone recommend anything to try, besides wiping and reinstalling my Ubuntu partition? I've been messing with this and googling for several hours, and I'm getting worn out.

Thanks.

---

### Post by teward on 2009-12-02
a thought:  try going into the terminal and doing this:

```
sudo ifconfig wlan0 up
```

See if that gets it to turn on.

---

### Post by colinnwn on 2009-12-03
I felt stupid for not thinking of that, but alas I tried and nothing happened. Enable wireless was still unchecked and greyed out. I'm not on that computer now, but the 2nd line of ifconfig wlan0 did say "UP BROADCAST ..." (can't remember the rest, and I'm not sure if that means it is really "up"). It also had't received an IP or DNS info from DHCP on my router.

---

### Post by colinnwn on 2009-12-04
I'm out of ideas and tired of no wireless. Are there any other forums I should ask about this on before I wipe and reload Karmic? Should I report it on Launchpad as a bug? I'm not sure what I'd say since I have no evidence what caused it, or idea about how it happened other than after some random system update.

Thanks.

---

### Post by mikewhatever on 2009-12-04
I've a silly idea. Is there a button to turn the wireless on and off? It actually happened to me a couple of times.

---

### Post by colinnwn on 2009-12-04
> **mikewhatever said:**
>  Is there a button to turn the wireless on and off?

Not a button, but a switch. I tried that, but it didn't work, and wireless was working in XP. I didn't think this would work, but I remembered people complaining about NetworkManager. 

I researched alternatives and installed [WICD]("http://help.ubuntu.com/community/WICD"). Wireless immediately started working again. I highly suggest trying it if wireless is giving you any trouble. I used to have occasional problems about networks not being available, but giving it a couple minutes, or restarting my computer always got connectivity back. I have a desktop that has been going very slow on wired internet (like 10 kbs on a 30 mbs line). I was planning on reinstalling Ubuntu on it too. I think I'm gonna try WICD on it before I do. Looks like NetworkManager really wasn't ready for prime time.

---

### Post by mikewhatever on 2009-12-04
Now that you've mentioned wicd, check out this bug report -> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440694](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440694)
Looks like the same problem on different hardware, and I haven't had that problem since installing wicd.

---

### Post by colinnwn on 2009-12-05
Thanks. I reported my problems in that bug. It will be interesting if they let that bug expire, or someone tries to look at it. 

The desktop I mentioned that had been connecting very slow on wired internet was also fixed by switching to WICD. I should have been more specific about how it was connected though. It is connected by ethernet wire, to a router that is connected to an internet access point wirelessly. So I'm not sure that had any affect on it and NM versus WICD. But I do know that it wasn't a general wireless problem, because 2 other computers were attached at the same time to the same router both wired and wirelessly and were having no problems.

I think I'm gonna get NM off the rest of my fleet of Ubuntu computers, before it causes me additional heartburn.

---

