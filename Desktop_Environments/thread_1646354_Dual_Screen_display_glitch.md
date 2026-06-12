---
title: "Dual Screen display glitch"
date: 2010-12-15
forum: Desktop Environments
---

### Post by LightSystem on 2010-12-15
Hi there, Ubuntu community.

Although this is my first post here, I have been an ubuntu/linux user for quite a while, but just recently I regained conscience from my 2 year Windows-induced coma and started using ubuntu as my sole OS.
So far my experience has been awesome! I have been able to tailor my system to my own specific needs and I am really happy with my setup.
However, there is just one small little thing that has been bugging me.

Right now I have a dual monitor setup, my laptop screen and an external one connected through the laptop's hdmi output. Screenshot:
[IMG]http://img818.imageshack.us/img818/408/screenshot1as.png[/IMG]

What the image doesn't show however, is that my first screen (left side) is kinda like "leaking" into my second screen (in the right side). What this means is that I can see a little bit of my left screen on my right screen in a vertical bar maybe 2-3 pixels wide, and where the 1st screen does not exist(on the top left of the 2nd screen), the bar becomes a random-color vertical pixel stripe. It's hard to describe and therefore hard to google this problem. That's why I am here to seek help. This problem is really annoying when I am, for example seeing a full screen video in my 2nd screen. Here is my xorg.conf:
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-LVDS"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1366x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 160"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1366 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-LVDS" "0-LVDS"
	Option	    "Monitor-DFP1" "0-DFP1"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2806 2806
		Depth     24
	EndSubSection
EndSection

Oh, one more thing, the problem occurs with the proprietary driver as well as the non-proprietary one.

Thanks

edit: Im using ubuntu 10.10

---

### Post by StarlitxEyes on 2010-12-15
Have you tried unplugging your monitors and replugging them in. My weird settings were fixed when i did that.

---

### Post by LightSystem on 2010-12-15
I have, and it's not generally a good idea. Hot plugging and unplugging the external monitor results in pretty random behaviour. Just now I tried it and the screen just became black, and the windows would not display. I had to restart, and actually some more random behaviour ensued but now seems to be fine. I mean back to normal abnormality atleast.

---

### Post by LightSystem on 2010-12-16
Hasn't anyone seen this problem before? I will gladly explain it better if i was confusing before...

---

