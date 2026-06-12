---
title: "My Purchase, is M1330 and M1330n different in any way? I hope not!"
date: 2008-01-31
forum: Dell  Ubuntu Support
---

### Post by CorruptNoob on 2008-01-31
I just bought the following with the plan of removing vista and installing ubuntu, got the windows one because for some ungodly reason, it's £200 cheaper...


Item
	Description
Base
	Intel® Core&#153; 2 Duo Processor T7250 (2.00 GHz, 2 MB L2 cache, 800 MHz FSB)
Memory
	2048MB 667MHz Dual Channel DDR2 SDRAM [2x1024]
Keyboard
	Internal Lightweight Keyboard - UK/Irish (QWERTY)
Video Card
	128MB nVidia® GeForce® 8400M GS
Hard Drive
	160GB (5400RPM) SATA Hard Drive
Microsoft Operating System
	Genuine Windows Vista&#174 Home Premium - English
Modem
	No Modem
Optical Devices
	Fixed 8x DVD+/-RW Slim Slot Load Drive, including SW
Wireless Networking
	Intel® Pro Wireless 3945 802.11a/b/g Mini-Card - Europe - Core 2 Duo Processors
Shipping Documents
	English Documentation with English/Irish Power Cord
Gedis Bundle Reference
	N0113352
Microsoft Application Software
	Microsoft® Works 8.0 - English
Standard Warranty
	Base Warranty - 1 Year XPS Premium Hardware Support (incl. Gaming and On-Site Support)
Enhanced Service Packs
	Base Warranty - 1 Year Hardware Support, Next Business Day
Protect your new PC
	No Security/Anti-Virus Protection - English
Power Supply
	65W AC Adapter
Bluetooth
	Dell&#153; TrueMobile 355 internal Bluetooth Module - European
Order Information
	Inspiron Order - UK
Primary Battery
	Primary 9-cell Lithium-Ion Battery (85 WHr)
Carrying Cases
	No Carry Case
Biometric Identification
	Biometric Fingerprint Reader
Dell System Media Kit
	Resource DVD - (Diagnostics & Drivers)
Colour Choice
	Midnight Blue & 0.3 mega pixel Camera for White-LED Display
Accidental Damage Support
	No Accidental Damage Support
Online Promotion Option for GEDIS Configs
	Dell Internet Order.
LCD
	13.3" UltraSharp&#153; WXGA (1280x800) White-LED Display (300 nits) with TrueLife&#153;
Price:
	£ 619.84
Delivery Charge:
	£ 0.00
VAT:
	£ 108.47
Total Price:
	£ 728.31

---

### Post by fragos on 2008-02-01
I have a 1420n and I believe the only differences other than sticker was what options were offered.  Options for the n were selected based on Ubuntu compatitibility.  The 1330 you listed has options that are well supported by Ubuntu.  You should be fine.  I'm not sure if the bluetooth will work without some tweaking.

---

### Post by CorruptNoob on 2008-02-02
> **fragos said:**
> I have a 1420n and I believe the only differences other than sticker was what options were offered.  Options for the n were selected based on Ubuntu compatitibility.  The 1330 you listed has options that are well supported by Ubuntu.  You should be fine.  I'm not sure if the bluetooth will work without some tweaking.

does the dell wireless-n card work with ubuntu?

---

### Post by fragos on 2008-02-02
> **CorruptNoob said:**
> does the dell wireless-n card work with ubuntu?

The wireless card you have is the Intel which worked out of the box on my 1420n.  The Intel wireless is well supported.  It picked up more signals than my friends laptop.  I also got the 9 cell battery option which gives me over 5 hours of service and charges from dead in two hours.  My 1420n came with 7.04.  When Dell started shipping 7.10 I was able to download the Dell version ISO which was large enough to require a DVD.  You may be able to download the Dell 7.10 for your 1330.

---

### Post by fairyliquidizer on 2008-02-02
does DVD playback on 7.10 get locked in some way so users who buy a Ubuntu 1330 can play it but those installing it on a Vista 1330 cannot?

Just wondering as I am tempted to get one of these (other options are MacBook or Asus EEE).

THanks,
Fairy

---

### Post by rogi on 2008-02-02
I have a M1330 dual booting Ubuntu (yea) and Vista (boo). Everything works great.  DVD, Wi-Fi, Bluetooth, etc.   I don't have the N-card so I can't speak to that.  

Main things I notice are:
The Wi-Fi driver is not quite as strong on keeping weak signals, but works well if you have decent coverage.  I say the driver, b\c the Vista load can keep the connection a bit better.  However, it does allow most of the 'tools' for wireless to work with the card.

Brightness - when I dim the brightness for low light, it jumps back to full brightness after a few minutes.

DVD playback, I had to load few extra packages, but works well.  I'll see if I can find the post/guide for it.

---

### Post by fairyliquidizer on 2008-02-02
Does the nVidia graphics card generate more heat/noise?  I'm not sure that the add on graphics card is that important to me.

Trying to work out the right spec.

What are the speakers like on it?  System noises only or good enough for music in hotel rooms.

---

### Post by cendant on 2008-02-02
If you change the wireless module, then you will not experience any problems with WiFi at all

>>> ipw3945 Wireless Network Module Issues


Add to /etc/modprobe.d/blacklist-ipw3945:

blacklist ipw3945

Add to /etc/modules: 



iwl3945





>>> Hardware encryption for the iwl3945 module



Add to /etc/modprobe.d/iwl3945:


options iwl3945 hwcrypto=1

---

### Post by fragos on 2008-02-02
I decided to try this and it still works on my home wireless.  We'll have to see if there are any improvements when I use the network I had occassional issues with.

---

### Post by rogi on 2008-02-02
I don't notice any difference in Vista vs Ubuntu with noise or heat from the card.  As for the nVidia card vs. say an Intel card, the better supported 3D in nVidia was worth it to me.  Heat dissipation is good on this for such a thin form factor.  I frequently leave it on my lap with no problem due to how the battery keeps it elevated slightly.

Battery life is about 5.75 hrs with the back light (LED) dim and watching a DVD in either Vista or Ubuntu. With the screen full bright, it's just over 2.5 hrs.  I don't think the extra graphics hurts it here. 

Speakers are mediocre IMHO - they are loud enough to hear in the house as long as my 2yr old doesn't start running around trying to talk.  I typically use the head phones unless just listening to background music.

---

