---
title: "Samsung syncMaster 997df Resolution Problem"
date: 2005-06-26
forum: Desktop Environments
---

### Post by LordKaT on 2005-06-26
Heyah, I'm having some problems getting my Syncmaster 997df acting properly under Ubuntu (Gnome).

My problem is that I'm unable to set the monitor into 1600x1200 mode (which is actually the recommended resolution). The Horiztonal Sync and Vertical Referesh rates are according to Samsung's spec.

The login screen does display 1600x1200; however, the desktop displays in 1024x768, with some weird wraparound problem - the top portion appears to redraw on the bottom, so anything below is obscured.

The commented out HorizSync and VertRefersh works up to 1024x768.

Any help is appriciated.

> 
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Samsung"
	ModelName "SyncMaster 997DF"
	#HorizSync 30-66
	#VertRefresh 56-85
	HorizSync 30-96
	VertRefresh 56-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Monitor		"Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

---

