---
title: "Max Resolution 600x800"
date: 2008-12-07
forum: General Help
---

### Post by marco.voormolen on 2008-12-07
Goodday all,

I just installed ubuntu on my grandfather's computer, but I'm having problems with the resolution settings. I dont seem to be able to set a resolution higher than 600x800 (while I was able to do so in windows).

The gfx card is onboard:


> id:	
display
description: 	VGA compatible controller
product: 	KM400/KN400/P4M800 [S3 UniChrome]
vendor: 	VIA Technologies, Inc.
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	01
width: 	32 bits
clock: 	66MHz
capabilities: 	pm agp agp-2.0 bus_master cap_list
configuration:	
latency	=	32
mingnt	=	2

My Xorg file is as follows:

> 
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

I have no experience with installing drivers manually whatsoever. I just did over 2 hours of googling but haven't been able to find a proper solution yet. I hope some will be able to help me.

Thanks in advance!

---

### Post by marco.voormolen on 2008-12-08
Anyone?

---

