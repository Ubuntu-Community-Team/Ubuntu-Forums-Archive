---
title: "How do I change the resolution in NWN?"
date: 2008-04-16
forum: Gaming &amp; Leisure
---

### Post by SandmanXC on 2008-04-16
I have installed NWN, and got it to work, sound and all. I also made run in windowed mode, but the window is to large, and is unresizable. When I try to change the resolution in-game, the only option is 1280*800. I believe it has something to do with xorg.conf, but I'm not willing to experiment on my own :D. Please advise!

---

### Post by Perfect Storm on 2008-04-16
please post your xorg.conf

---

### Post by SandmanXC on 2008-04-16
```

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x800"
	EndSubSection
EndSection

```

Should I add more modes or something? I would like some clear instructions cause I don't want to screw it up :D

---

### Post by DarkSim on 2008-04-16
There is a file called nwn.ini in your NWN directory. You can change it from there by changing these two lines:

Height=864
Width=1152


Change the numbers to whatever you need. Those numbers are what I use for a  1152*864 window on a 1280*1024 monitor.

---

### Post by SandmanXC on 2008-04-16
I tried that but it made no difference. Any other ideas?

---

### Post by Perfect Storm on 2008-04-16
> **DarkSim said:**
> There is a file called nwn.ini in your NWN directory. You can change it from there by changing these two lines:

Height=864
Width=1152


Change the numbers to whatever you need. Those numbers are what I use for a  1152*864 window on a 1280*1024 monitor.

yeah, but it wont help if the resolution is supported in xorg.conf

try add the resolution you want to your xorg.conf, note a resolution that also is supported by your monitor.

add it to allready existing line of 		Modes		"1280x800"

---

### Post by SandmanXC on 2008-04-18
That didn't help either. I also tried making video modes for 32 screen depth, and I tried to change NWN depth to 24. Nothing worked.. Any other suggestions?

---

