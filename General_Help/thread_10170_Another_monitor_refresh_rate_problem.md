---
title: "Another monitor refresh rate problem"
date: 2005-01-05
forum: General Help
---

### Post by kez on 2005-01-05
Hello all,

I installed Ubuntu yesterday and I have to say I'm really pleased with it. There is just one glitch, which isn't a showstopper but which has me puzzled.

I have an HP Pavilion MX70 monitor, which has been correctly recognised according to XF86Config-4. Currently it will only give me 60Hz at 1280x1024 and 1280x960. This gives me serious eyestrain, so I'm using 1024x768 at 85Hz at the moment. I know I can get a higher refresh rate at 1280x1024 because I did when I ran SuSE 9.2 before installing Ubuntu.

After browsing this forum, I've tried the following:

Editing refresh rates according to manufacturer's specs in /etc/X11/XF86Config-4, and altering the default colour depth to 16 from 24 in the same file, just in case that made a difference (it didn't so I altered it back). I've also tinkered with sudo dpkg-reconfigure xserver-xfree86 which didn't make any difference, though I didn't really change any information as it was seemingly all correct. I've even done a fresh install just to make sure it wasn't some kind of installation bug. I have a Nvidia GeForce3 card but I haven't installed any specific Nvidia graphics drivers as I've used the default nv driver with good results in the past on SuSE, not requiring 3D acceleration, so I assume that Ubuntu is similar in this regard. I've also tried checking with the live CD, but this identified my monitor as an HWP0503, which I don't think is right. 

I've reached a stalemate. Like I say, this isn't a major problem, it's more the not-knowing that's annoying me. Perhaps wiser minds could give me the benefit of their knowledge? What am I missing, or haven't I done?

Thanks,
Kez  :) 

**UPDATED TO ADD:** *OK, call me a dufus with bad eyesight. After some more research, I discovered 60Hz was fine for the monitor at 1280x1024 - it was the colour depth (now set to 16) that made all the difference. Guess my eyestrain was worse than I thought... Ubuntu still reigns!*  :mrgreen:  

I enclose the *(now no longer)* relevant snippet of my XF86Config-4:

Section "Monitor"
	Identifier	"MX70"
	HorizSync	30-70
	VertRefresh	50-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV20 [GeForce3]"
	Monitor		"MX70"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

---

