---
title: "Dual Screen works in 8.10 but not in 9.04"
date: 2009-06-07
forum: Desktop Environments
---

### Post by addict[B] on 2009-06-07
Hi,

I just upgraded to 9.04 from 8.10. Previously I had a 19" monitor attached to my laptop and was running dual screen quite happily with the ATI BigDesktop setup. Unfortunately I can't make the same thing happen on Jaunty and I'm at a bit of a loss.

When I set this up in Intrepid I used a really good howto which covered all aspects of dual screening for many different graphics cards, drivers etc. but I haven't been able to find this again.

My Xorg.conf file looks like this:

> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 800
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection


My hardware is an Acer Ferrari 4002 with an ATI mobility Radeon X700

lspci gives this for my graphics driver:
> 01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
        Subsystem: Acer Incorporated [ALI] Device 007e
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>


Unfortunately I have no idea what this means.

I have had limited success with "Configure display settings" but I can only set my second monitor to a maximum resolution of 1024x768 when it should be 1440x900.

Any help/pointers would be much appreciated, cheers.

---

