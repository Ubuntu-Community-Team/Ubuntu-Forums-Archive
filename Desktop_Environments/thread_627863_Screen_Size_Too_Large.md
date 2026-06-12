---
title: "Screen Size Too Large"
date: 2007-11-30
forum: Desktop Environments
---

### Post by Katydid5283 on 2007-11-30
Hi! I seem to have a virtual resolution problem that I cannot fix. About 5% of my screen is cut off on each side when I use my S-video connection to hook up my television. I have tried adjusting the virtual resolution to no avail.

This is what I tried:

ection "Screen" 
	Identifier	"Default Screen" 
	Device		"nVidia Corporation G80 [GeForce 8500 GT]" 
	Monitor		"Generic Monitor" 
	Defaultdepth	24 
		SubSection "Display"
			Depth 24
			Modes "1200x1024" "800x600"
		EndSubSection
EndSection

I thought what I was doing is setting the actual resolution to a large size, and the virtual resolution too small (I was hoping for underscan, so I could adjust from ther) The result was the screen was still much to large.

I've also tried several different resolutions, but with the same result.

I've also set the virtual resolution higher than the actual, and the result was far worse.

This is my current setup - has anyone else had this trouble with S-video and virtual resolution? 

Section "InputDevice" 
	Driver		"wacom" 
	Identifier	"cursor" 
	Option		"Device"	"/dev/input/wacom" 
	Option		"Type"	"cursor" 
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY 
EndSection 

Section "Device" 
	Identifier	"nVidia Corporation G80 [GeForce 8500 GT]" 
	Driver		"nvidia" 
	Busid		"PCI:5:0:0" 
	Option		"AddARGBVisuals"	"True" 
	Option		"AddARGBGLXVisuals"	"True" 
	Option		"NoLogo"	"True" 
EndSection 

Section "Monitor" 
	Identifier	"Generic Monitor" 
	Option		"DPMS" 
	Horizsync	30-70 
	Vertrefresh	50-160 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Device		"nVidia Corporation G80 [GeForce 8500 GT]" 
	Monitor		"Generic Monitor" 
	Defaultdepth	24 
		SubSection "Display"
			Depth 24
			Modes "800x600"
		EndSubSection
EndSection 

Cheer
Kate

---

### Post by phidia on 2007-11-30
i don't know if it will work for you but you can try xvidtune (type that in a terminal window) you may need to use sudo to get changes to stick-therefore "sudo xvidtune" it didn't work for me with a lcd tv as a monitor but maybe you'll have better luck?

---

### Post by TeaSwigger on 2007-11-30
Perhaps a silly question, but are you accounting for overscan? Unfortunately all consumer televisions crop 5-10% or so of the image on all sides while computer monitors do not. This is part of the television standards, done in order to reduce the chances of side artifacts appearing on screen (largely from the analog TV antenna days, but still carried over). You could have your television recalibrated and may be able to minimize this overscan, but be aware you could find side artifacts on programming since it's assumed all televisions will be using generous amounts of cropping / overscan.

Appologies if you already know all that.

---

### Post by Katydid5283 on 2007-12-01
Actually, I didn't know that! I'll bet that is the problem; this is the second television I have had this problem on, and (as I probably should have mentioned) the screen looks beautiful on my LCD monitor when it was connected.

Thanks for clearing that up!

Cheers
Kate

---

