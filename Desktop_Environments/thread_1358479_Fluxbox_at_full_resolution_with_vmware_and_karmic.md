---
title: "Fluxbox at full resolution with vmware and karmic"
date: 2009-12-18
forum: Desktop Environments
---

### Post by alankennedy100 on 2009-12-18
Hi

I am using Karmic Ubuntu on vmware and have installed fluxbox. I can get the GNOME desktop at full resolution (1280 x 800), but not fluxbox. By default fluxbox will boot with 800 x 600

I've tried creating a basic xorg.conf in /etc/X11 (Karmic didn't come with one) but the maximum resolution I get is 1280 x 720. Logging into GNOME when the xorg.conf is there it also only offers that resolution.

Any ideas on what I can do with xorg.conf so that I can have full resolution in both GNOME and fluxbox.

Bellow is the xorg.conf I've tried

Thanks,

Alan

Section "Device"
	Identifier	"Configured Video Device"
	Driver "vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Subsection "Display"
		Depth 24
		Modes "1280x800"
	EndSubSection
EndSection

---

### Post by Jurpofi on 2010-03-10
Your problem might be a lack of video memory. Add more video memory to your virtual computer and see if it helps.

---

