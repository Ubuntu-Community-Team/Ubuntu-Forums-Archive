---
title: "Can't set permanent refresh rate"
date: 2011-12-28
forum: Desktop Environments
---

### Post by ACupOfCoffee on 2011-12-28
I'm trying to get the refresh rate on my monitor set to a permanent 85Hz. I can set it there for a single session only. CompizConfig won't change it. I set ~/.xprofile to where it will set the correct refresh rate when I run it and even put it in startup programs. I tried editing xorg.conf. Under the section "monitor" I put the following
```
# 1024x768 @ 85.00 Hz (GTF) hsync: 68.60 kHz; pclk: 94.39 MHz
  Modeline "1024x768_85.00"  94.39  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync
```but it doesn't seem to do anything. I tried taking out the pound sign thinking that commented it out, but I couldn't boot. I had to do some funny stuff to be able to get to a command line so I could open it up in vim and put the pound sign back in. I know the modeline is correct because it works if I select it from grandr.

What do I have to do so I don't have to manually run ~/.xprofile every time I boot up my computer to get a flicker free display?

---

### Post by ubix on 2011-12-28
As far as I know the format for Monitor section is as follows:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection
```

Mode parameter is in Display sub-section of Screen section e.g.:```
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
        # o o o
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

---

### Post by ACupOfCoffee on 2011-12-30
So in my case would I put[FONT=monospace]
[/FONT]```
HorizSync    68.60
VertRefresh    85
```under monitor section?

Also, I noticed that the login screen looks fine. It looks like it's set to a proper 85 until I log in. Would that give anyone a clue as to where my setting is being overridden?

---

