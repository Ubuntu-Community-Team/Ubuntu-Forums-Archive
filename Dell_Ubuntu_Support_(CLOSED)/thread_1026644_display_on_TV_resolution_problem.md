---
title: "display on TV: resolution problem"
date: 2008-12-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chug on 2008-12-31
Hi,

I use a dell inspiron 1525 with 8.04 (hardy). When I plug the cable and press the Fn+crt/lcd keys, the TV display partially what I see on the laptop. 

To my understanding, the resolution of the laptop change. Well in fact only the "taskbar" change (reduce), all the other windows stay wider (it looks strange). If the application (in this case movie) is wider than the supposse new resolution (shown by the taskbar size), it is not working (specially true if I ask to see fullscreen for a movie).

Any idea how to fix that?

thx by advance
hugo

ps: here is my xorg.conf

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"monitor-TV"	"TV"
EndSection

Section "Monitor"
	Identifier	"TV"
	Option		"Ignore"	"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"Ignore"	"false"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

---

### Post by chug on 2009-01-03
I found a workaround today. I disable all gnome "visual effect" and it works (I don't know why).

To do it, go to System->Preferences->Apparence on the visual effect panel and choose no visual effect.

Note that I also install grandr that help me a lot to configure the resolution of the TV.

---

