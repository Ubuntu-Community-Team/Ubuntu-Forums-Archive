---
title: "Kubuntu - Resolution Issue"
date: 2006-08-03
forum: Desktop Environments
---

### Post by BarfBag on 2006-08-03
My LCD acts weird with resolutions higher than 1024x768.  When I "auto-center" it, it goes off to the side half way.  I usually just change my resolution and it's fixed.  This time, I auto-centered KDM not thinking.  It carried over to the desktop.  The KMenu is all the way to the left, so I can't see a thing.  I think my best bet is doing something via Ctrl-Alt-F1.  How do I change the resolution for KDM and KDE?

Thanks,
BarfBag

---

### Post by wieman01 on 2006-08-04
You need to configure your x-server config file:
> 
sudo gedit /etc/X11/xorg.conf

This is the relevant section:
> Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"Philips 170B"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1024x768"
	EndSubSection
EndSection

"DefaultDepth" represents the SubSection you want to make use of. Then choose the resolution you want and delete the remaining ones that you don't need from the relevant line.

E.g.:
> 	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection

Does that help?

---

