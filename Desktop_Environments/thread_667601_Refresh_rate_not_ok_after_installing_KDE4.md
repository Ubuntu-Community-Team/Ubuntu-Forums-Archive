---
title: "Refresh rate not ok after installing KDE4"
date: 2008-01-14
forum: Desktop Environments
---

### Post by atlefren on 2008-01-14
Hello 

Recently the refresh rate on my kubntu install is all messed up. It says 60Hz in "Monitor & Display" in System Settings, and i've run dpkg-reconfigure xserver-xorg 4-5 times.. Still the screen is "flickering" (i see it especially on large images and such).

The computer is a Toshiba tecra A2 with an intel graphics card. I've installed 915resolution, and are currently using a resolution of 1400*1050, but the flickering is present at other resolutions too..

This problem started after installing KDE 4.0, i've installed RC1 & 2 before without trouble, and i've been running kubuntu on the machine for 7-8 months. In win xp, the screen is working perfectly at 60Hz..

The strange thing is that the problem is there when i try to boot from the kubuntu 7.10 live cd.. 


here is the part from my xorg.conf that I think is relevant
[PHP]
Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82852/855GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection
[/PHP]


I really hope someone can help me out with this, as my eyes now long for windows and a working refresh rate..

---

