---
title: "Screen Resolution"
date: 2006-02-01
forum: Desktop Environments
---

### Post by varland on 2006-02-01
I've just installed Linux for the first time, and things are going mostly okay, but I have a few issues I can't get fixed...

I have a Dell OptiPlex GX 270 with Intel Integrated graphics (In the Device Manager, it shows up as "82865G Integrated Graphics Device"). I also have a Dell 2005FPW widescreen LCD (optimal resolution: 1680 x 1050).

I can't get the display resolution above 1280 x 1024. I've searched online and in various forums, but can't find anything that's worked. Obviously I know the card is capable of this resolution, because Windows XP has been running at 1680 x 1050 happily for months.

Please point me in the right direction. I really like Ubuntu so far, but if I can't utilize my monitor, I'll be forced to try something else...

Thanks in advance.

---

### Post by handy on 2006-02-02
I don't know what you've read or tried?

The following works for many, me included:  

Edit the **xorg.conf** file to suit, **only after having made a backup**  
I just add .bak on a copy in the same directory for any system files that I modify, I can allways find them then.:mrgreen: 

OK, in the terminal enter the following:

**$sudo gedit /etc/X11/xorg.conf**

Then find the following section in the **xorg.conf** & edit the **Vertical Sync** & **Horizontal Refresh** Rates, to suit your monitor, if you don't have a manual then go to the manufacturers site, Google for the info' if you have to.  They need to be accurate ranges.  So, look for  

[B]HorizSync
VertRefresh[/B]

In the copy of the relevant section of my **xorg.conf** below, you will see the appropriate ranges for my Sony 19" CRT monitor, they **won't** suit your monitor. 
----------------------------------------
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	***30-107***  
	VertRefresh	***48-120***
EndSection
----------------------------------------

Then the next section of the **xorg.conf**, shows you the screen **Modes** & there settings:  Follow the format consistantly & add any valid screen resolutions that you need to use.

----------------------------------------
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"**1600x1200, 1280X1024, 1024X768, 800X600, 640X480**"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"**1600x1200, 1280X1024, 1024X768, 800X600, 640X480**"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"**1600x1200, 1280X1024, 1024X768, 800X600, 640X480**"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"**1600x1200, 1280X1024, 1024X768, 800X600, 640X480**"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"**1600x1200, 1280X1024, 1024X768, 800X600, 640X480**"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"**1600x1200, 1280X1024, 1024X768, 800X600, 640X480**"
	EndSubSection
EndSection
----------------------------------------
If after that you are still in trouble go here:

[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

All the best...:KS

---

