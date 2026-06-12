---
title: "How do i change the screen Resolution in ubuntu 9.04?"
date: 2009-05-04
forum: General Help
---

### Post by imthepod on 2009-05-04
How do i change the screen Resolution in ubuntu 9.04?


i wanna change it to 1024 x 768, the highest i can set it to is 800 x 600, can anyone help please? i tried going into System>Administration>Hardware Drivers but theirs nothing their to be installed

NOTE: for those who don't know anythng abou it, its not like windows

---

### Post by freonchill on 2009-05-04
whats your video card?

---

### Post by DJonsson2008 on 2009-05-04
If you have an Nvidia card and proprietary drivers loaded,
I think Nvidia provides a utility for setting the resolution,
nvidia-settings or and equivalent, I'm not on my 9.4 machine
at the moment so can't verify the module's name.

In the past I used gnome display config for a GUI to change
the resolution on 8.4., but after that broke for some reason,
I found a simple edit of /etc/X11/xorg.conf directly 
would do the trick.

You will need to know your monitors Horizsync/Vertical 
refresh ranges to make it work, via the manual edit
method.

Ie. I've overwritten these sections in my xorg.conf for my AcerAL1916W 

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Acer"
	Modelname	"Acer AL1916W"
	Horizsync	30.0-82.0
	Vertrefresh	56.0-76.0
  modeline  "1024x768@76" 76.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
		Modes		"1024x768@76"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

---

