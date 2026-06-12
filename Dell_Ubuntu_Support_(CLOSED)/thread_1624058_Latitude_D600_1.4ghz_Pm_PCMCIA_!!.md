---
title: "Latitude D600 1.4ghz Pm PCMCIA !!"
date: 2010-11-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MACE1 on 2010-11-17
I have a Buffalo PCMCIA WLI-PCM-L11 802.11b wifi card for my DELL.
As XP has got so slow and bloated and I want my laptop back I Wiped it and installed Ubuntu 10.04. Everything works OK as far as I can determine with the exception of the WiFi PCMCIA and Smart Card Reader.
It does not seem to matter what PCMCIA device I put in, there never seems to be a driver. Tried 10/100 Network card and a Bluetooth Card.
From research I see that in the past users have got this card working but nothing to date is working for my setup.

The socket looks to be OK as devices do light up but no drivers:
Socket 0:
  5.0V 16-bit PC Card
Socket 1:
  5.0V 16-bit PC Card
  Subdevice 0 (function 0) [unbound]

~$ lspcmcia
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.0)
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:02:01.1)
Socket 1 Device 0:	[-- no driver --]	(bus ID: 1.0)

As I am very unfamiliar with the process of adding drivers into Linux, I would appreciate 'gentle' guidance on how to rectify this problem.
I see some recommend using a wrapper for windows drivers. I have working drivers for XP but I do not know which parts are required for the purpose and it does seem the card should be supported natively.

If anyone knows of URL's which pertain to Ubuntu 10.04 please post them.:confused:

One other minor request: Anyone know how to get the 3 volume buttons adjacent to the power button to function ?

---

