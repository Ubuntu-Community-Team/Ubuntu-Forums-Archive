---
title: "Dell Double finger scrolling"
date: 2008-11-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by memoires on 2008-11-10
I recently installed Ubuntu 8.10 on my Dell Inspiron 640m. From what i know, it has synaptic touch pad. Basically, when i use 2 fingers to scroll, the scrolling works fine sometimes, but most of the time, it jumps from top to bottom of a page if i'm scrolling up and vice versa. I don't know what i'm doing doing. Suggestions would be appreciated! :)

My Xorg.conf looks like this:-

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "CorePointer"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizScrollDelta" "0"
	Option "VertTwoFingerScroll" "true"
	Option "HorizTwoFingerScroll" "true"
	Option "TapButton2" "3"
	Option "TapButton3" "2"
	Option "SHMConfig" "true"
EndSection

---

