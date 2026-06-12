---
title: "SoftGate(Quetec driver)"
date: 2006-03-03
forum: Desktop Environments
---

### Post by ontheinside on 2006-03-03
My WLAN PCMCIA card is not supported by ubuntu. So I decided that I wanted to install ndiswrapper and use the windows drivers provided with my card on CD. However, when I searched the CDROM for the windows *.inf file I could not locate it anywhere.
I searched google for a Windows* driver everywhere and could not find one. I also searched for a linux driver and could not find that either. I went to the companies website and they no longer own the domain and hence I cannot download a driver from them.
If my card is not supported by ubuntu and I cannot locate a win driver, then what am I supposed to do?
You think the CD would have a driver somewhere on it, but i searched every directory and could not find one. All i found were auto setup files....
HELP! I just bought this card **[SIZE="4"][SIZE="4"]brand new[/SIZE][/SIZE]** and would like to use it!!:cry:

---

### Post by RAOF on 2006-03-03
I hate to say it, but if you've just bought it brand new, why didn't you check to see if it was supported first?  You could've bought a wireless card that worked out of the box! :???: 
One of the best ways to get linux support for hardware is to specifically buy hardware **with** linux support.  It's a free-market way to get good linux drivers ;)

Anyway, now that you've got this one...  Do you have a windows machine you could use to extract the drivers?  If you do, just use the autorun to install the drivers - they'll end up under \windows\system32\.  You could then copy the needed files from there.

Alternatively, if you've got the reciept...  Why not return it, and get a card that **is** supported by linux?

Here's a list of supported cards, from [this site]("http://pcmcia-cs.sourceforge.net/ftp/SUPPORTED.CARDS"):
```

Wireless network adapters:

	[airo_cs driver] [x86]
	Aironet PC4500, PC4800
	Cisco 340, 350
	Xircom Wireless Ethernet Adapter

	[netwave_cs driver] [x86]
	Breezenet SA-PX
	Xircom CreditCard Netwave

	[ray_cs driver] [x86,axp]
	BUSlink Wireless LAN Adapter
	Raytheon Raylink
	WebGear Aviator 2.4, Aviator Pro

	[wavelan_cs driver] [x86,smp]
	AT&T / NCR / Lucent WaveLAN version 2.0
	DEC RoamAbout/DS

	[orinoco_cs driver] [x86,axp,ppc,smp]
	[ this driver supports multiple chipsets and some features may
	not be supported for all cards ]
	3Com AirConnect
	1stWave 1ST-PC-DSS11IS, DSS11IG, DSS11ES, DSS11EG
	Actiontec HWC01170-01/802C12
	Adaptec ANW-8030
	Addtron AWP-100
	Airvast WN-100
	Ambicom WL1100 PC
	ARtem Onair ComCard STD & EMB versions, 128- & 64-bit
	ASUS SpaceLink WL-100
	Avaya World Card
	Belkin F5D6020 [only Version 1]
	Buffalo WLI-PCM-S11
	Cabletron/Enterasys RoamAbout 802.11 DS
	Compaq WL100, HNW-100
	Conceptronic CON11Cpro
	Corega PCCA-11, PCC-11
	Dell TrueMobile 1150 Series
	D-Link DRC-650, DCF-650W, DWL-660, DCF-660W
	D-Link DWL-650 [older version, NOT new CardBus ones or 650+]
	EagleTec ET-WL300NE-CC
	Efficient SpeedStream SS1021 [old 16-bit, NOT new CardBus ones]
	ELSA AirLancer MC-11
	Ericsson WLAN Card C11
	Farallon SkyLINE
	HP F2136B
	HyperLink Wireless
	IBM High Rate Wireless LAN
	Intel PRO/Wireless 2011
	LA4111 Spectrum24 Wireless LAN
	Linksys WPC11 Instant Wireless [ NOT the CardBus v4 card ]
	Linksys WCF12 Wireless CompactFlash
	Lucent Orinoco WaveLAN/IEEE 802.11(b)
	Melco WLI-PCM-L11, WLI-PCM-L11G
	Microsoft MN-520
	NCR WaveLAN/IEEE 802.11
	Netgear MA401RA
	Nortel Networks eMobility
	Planet WL-3550
	PLANEX GeoWave GW-CF110, RoadLannerWave GW-NS11H
	Proxim Harmony 802.11b
	Safeway Wireless
	Samsung 11Mbps WLAN
	Sandisk Connect SDWCFB-000
	Seg Communications XI325H
	SMC2632W, SMC2532W-B
	Sohoware NCP110 Netblaster II
	Tekram AIR.mate PCF 200
	ZCOMAX AirRunner/XI=300

```

---

### Post by ontheinside on 2006-03-03
I think I will install the drivers on another windows laptop and then e-mail them to myself from that machine.
Then all i have to do is install ndiswrapper and use the drivers i dled from my email on my linux box. Hopefully this works. If it doesn't i guess i will just have to buy a new card that is already compatable. Thanks for the list of compatable cards. Hopefully i won't have to use that list and buy a new card.
I don't know why I didn't check to see if the card was compatable in the first place. I guess Im just used to windows where anything you buy will be compatable. I guess that is one of the down sides of being a Linux user.:(

---

