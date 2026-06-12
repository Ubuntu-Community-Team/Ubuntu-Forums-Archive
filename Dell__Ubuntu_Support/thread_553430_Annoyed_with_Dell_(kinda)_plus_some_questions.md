---
title: "Annoyed with Dell (kinda) plus some questions"
date: 2007-09-17
forum: Dell  Ubuntu Support
---

### Post by dardack on 2007-09-17
So back in July I bought an E1505 from Dell with Ubuntu pre-installed.  It's great.  love it.  My wife's laptop died so I needed to buy another laptop.  So went to buy another one (yes my wife uses Ubuntu on hers) but now I find you can only by the 14" one.  I mean what gives?  You can buy Windows in many many different sizes and flavors but we get 1, ONE, choice for laptop with Ubuntu, Hell i'd even love to buy one with no OS and no support, but NO you can't do that.  You have to buy windows.  So ok now my questions.

Since i don't want the 14" one, i'm thinking of getting the 17" one.  I know i have to get nvidia and the intel pro wireless.  Her eare the specs for the one I bought (and everything seems to work) and the 17 i am looking at to buy, and just want to make sure that everything will work with Ubuntu wihtout too much trouble:

17"
1	223-0957	Inspiron 1720, Intel Core 2 Duo T5250, 1.5GHz, 667Mhz 2M L2 Cache 	$1114.00
1	311-7217	1GB, DDR2, 667MHz 2 Dimm 	$0.00
1	320-5500	Anti-glare, widescreen 17.0 inch display (1440 x 900) 	$0.00
1	320-5467	128MB NVIDIA GeForce Go 8400 	$0.00
1	310-8474	Dell 926 Vista Printer Driver 	$0.00
1	341-4708	120G 5400RPM SATA hard drive 5400RPM 	$0.00
1	430-0493	Integrated 10/100 Network Cardand Modem, for Inspiron 	$0.00
1	341-4716	8X DVD+/-RW Dual Layer Drive 	$0.00
1	313-4783	Integrated High Definition Audio 2.0 	$0.00
1	430-2334	Intel 3945 WLAN (802.11a/g) Mini Card 	$0.00
1	320-5683	NO WEBCAM OPTION 	$0.00


15"
Inspiron E1505   	  Intel® Pentium® dual-core proc T2080(1MB Cache/1.73GHz/533MHz FSB
	[223-0459]
LCD Panel 	15.4 inch Wide Screen XGA Display with TrueLife&#153;(glossy)
	[320-4651]
Memory 	1GB Shared Dual Channel DDR2 SDRAM at 533MHz, 2 Dimm
	[311-7351]
Video Card 	256MB NVIDIA® GeForce® Go 7300 TurboCache&#153;
	[320-5634]
Hard Drive 	80GB 5400rpm SATA Hard Drive
	[341-3108]
Operating System 	Ubuntu Edition version 7.04
	[420-7153]
CD ROM/DVD ROM 	8X CD/DVD Burner (DVD+/-RW) with double-layer DVD+R write capability
	[313-3959]
Sound Options 	Integrated Audio
	[313-4217]
Wireless Networking Cards 	Intel PRO/Wireless 3945a/g
	[430-191


I guess i'm mostly concerned about the wireless card:
Intel 3945 WLAN (802.11a/g) Mini Card 	$0.00 for 17" compares to
Wireless Networking Cards 	Intel PRO/Wireless 3945a/g

Same number but one sais Pro, one says WLAN.  I don't want to not have it work for the new laptop.  I am somewhat concerned with the audio also.  I just don't want to not get something that won't work.  I did pay extra for the nvidia and the intel wireless but to me was worth it if it works.

Thanks all for any help.

---

### Post by dardack on 2007-09-17
And Crap i just noticed that it's the Nvidia Go 8400, I know the :

GeForce 8400 GS 	0x0422
GeForce 8400M GT 	0x0426
GeForce 8400M GS 	0x0427
GeForce 8400M G 	0x0428

Are any of those the Go version or am i complete F'd?

---

### Post by tturrisi on 2007-09-17
Go here:
[http://www.dell.com/content/products/features.aspx/nseries_nb?c=us&cs=04&l=en&s=bsd&~ck=anavml](http://www.dell.com/content/products/features.aspx/nseries_nb?c=us&cs=04&l=en&s=bsd&~ck=anavml)
and config the exsct system you want w/out Windows and then install  Ubuntu from the live cd.

I recently got this one w/ the dell 1380 wifi (tomorrow I get rid of the 1390 & teplace it w/ a gigabyte atheros mini-pci-e adapter.  Cost 1365 w/ shipping & instant rebates.  You don't need a biz account w/ del to buy there, you can purchase as "Guest".

```
PROCESSOR	Intel® Core&#8482; 2 Duo T7300 (2.00GHz) 4M L2 Cache, 800Mhz Dual Core	edit
OPERATING SYSTEM	FreeDOS Operating System Kit	edit
LCD PANEL	15.4 inch Wide Screen WXGA LCD Panel	edit
MEMORY	2.0GB, DDR2-667 SDRAM, 2 DIMMS	edit
HARD DRIVE	80GB Hard Drive, 9.5MM, 7200RPM	edit
OPTICAL DRIVE	8X DVD+/-RW Data Only	edit
VIDEO CARD	256MB NVIDIA® Quadro NVS 140M&#8482;	edit
WI-FI WIRELESS CARD	Dell Wireless&#8482; 1390 802.11g Mini Card	edit
PRIMARY BATTERY	9 Cell Primary Battery	edit
PRIMARY POWER OPTIONS	90W A/C Adapter	edit
```

---

### Post by dardack on 2007-09-17
Well i wanted a 17" i did end up ordering the 1720 or something like that.  I see that the wireless is the same, just the nvidia is what makes me nervous now, since i do play WoW on linux.  We'll see how it goes, maybe nvidia will develop that soon.

EDIT: This gives me hope:
[http://www.linlap.com/wiki/IBM-Lenovo+Thinkpad+T61](http://www.linlap.com/wiki/IBM-Lenovo+Thinkpad+T61)

EDIT again (sorry): I see you didn't upgrade to the intel wireless, can you tell me why? I thought the dell wireless had issues?  I know the intel one is under my restricted drivesr and when you buy ubuntu they make you get the intel one.  Just wondering if i spent $29.00 too much for the intel one.

---

### Post by Mavtech on 2007-09-17
Intel only has one 3945 chip.  You are ok.  I have the 3945 in my E1505.  It works "out of the box" with 7.04.  No drivers to install.

---

### Post by tturrisi on 2007-09-18
fyi-
The dell 1390 is cheaper, has a broadcom chipset & works well w/ the nayive bcm43xx kernel griver and bcm-fwcutter, ir it works well w/ ndiswrapper.  It's a mimi-pci-express card in these dell laptops, not a mini-pci.  I've ordered a Gigabyte atheros card to replace the dell 1390, much cheaper than the Intel card too.  [http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless-Cards/c42/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mPCIe-adapter/product_info.html](http://www.oxfordtec.com/us/MiniPCI-EXPRESS-Wireless-Cards/c42/p113/GIGABYTE-WI01GT-miniPCI-EXPRESS-Wireless-card---Atheros-Super-G-108-Mpbs-AR5005GS-mini-PCI-E,-mPCIe-adapter/product_info.html)

---

### Post by strabes on 2007-09-20
Get the intel wireless 3945. It works perfectly, always. Don't even mess with broadcom.

---

