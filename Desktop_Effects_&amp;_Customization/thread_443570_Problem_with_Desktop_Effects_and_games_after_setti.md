---
title: "Problem with Desktop Effects and games after setting up two monitors"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by mAIJK on 2007-05-14
Hey!
I found a way to get bigger resolution on my external monitor to my laptop. Now I have one desktop at each monitor, I LOVE IT!

BUT:
Since my changes Desktop effects doesnt work. And I no longer can run Counterstrike, It was not very good before but I had FPS 40-100. Now I got 2 FPS I think :)

Computer: Dell D600 1gb ram, Ubuntu 7.04, Radeon 9000. Think I still got the drivers that ubuntu came with. Tried to Install fglrx but my xserver just crash...

Here is a output from my Xconfig that I have changed:
> [SIZE="1"][I]Section "Device"
	Identifier	"0 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	Option "MonitorLayout" "LVDS,TMDS"
	BusID		"PCI:1:0:0"
	Screen 		0
EndSection

Section "Device"
	Identifier	"1 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Driver		"ati"
	Option "MonitorLayout" "LVDS,TMDS"
	BusID		"PCI:1:0:0"
	Screen 		1
EndSection

Section "Monitor"
	Identifier	"Primary Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Secondary Monitor"
	Option		"DPMS"
	Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062
EndSection

Section "Screen"
	Identifier	"Laptop Screen"
	Device		"0 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Primary Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"LCD Screen"
	Device		"1 ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
	Monitor		"Secondary Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

#Section "ServerFlags"
#   Option "Xinerama" "true"
#EndSection 

Section "ServerLayout"
	Identifier	"Default Layout"
       Screen      0  "Laptop Screen"
     Screen      1   "LCD Screen" LeftOf "Laptop Screen" 
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection[/I][/SIZE]

Need more info? Post a message and I will fill in! Really want help with this cuz Im loving my new xorg setup. I dont care so much for Desktop effects to be enabled but I really want Counterstrike and other games to work again!

Thank you alot
Best Regards
Micke

---

### Post by mAIJK on 2007-05-14
And if someone knows howto disable clearlooks I would be glad. I got clearlooks on my external monitor but not on my lappy monitor

---

