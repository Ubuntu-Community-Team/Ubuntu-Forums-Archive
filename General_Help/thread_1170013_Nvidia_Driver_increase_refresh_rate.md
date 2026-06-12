---
title: "Nvidia Driver increase refresh rate"
date: 2009-05-25
forum: General Help
---

### Post by burakvarhan on 2009-05-25
Hello,

I am using Ubuntu 9.04 and Geforce Go 7400 graphics card is installed on my laptop. **Without** enabling Ubuntu Nvidia Accelerated Graphics Driver my machine works with 70Hz refresh rate. However when I installed the Nvidia Graphics Driver the refresh rate diminishes to 60Hz and by no means I could change it.

I would like to ask if it is possible to boost the refresh rate with Nvidia Graphics Driver by modifying xorg.conf file and how to do it?

My current xorg.conf file which works perfectly with 70Hz is below:

[COLOR="DarkGreen"]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	# Power saving mode
	Option		"DPMS"
	HorizSync       30 - 110
	VertRefresh     50 - 150
	#1280x800 @ 70.00 Hz (GTF) hsync: 58.31 kHz; pclk: 98.89 MHz
	Modeline "1280x800_70.00"  98.89  1280 1352 1488 1696  800 801 804 833  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
	SubSection "Display"
		Modes	"1280x800_70.00"
	EndSubSection
EndSection[/COLOR]

---

### Post by izizzle on 2009-05-25
You really shouldn't modify the refresh rate. Too high and it can be bad for your monitor.

---

