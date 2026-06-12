---
title: "Mouse scrolling on toshiba laptop"
date: 2006-06-25
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-06-25
OK; I know there's a bunch of threads on getting the touchpad working with scrolling already, but I've spent hours trying, not getting it to work. (SuSE got it working out of the box, both vertical and horizontal scrolling, though I really only need the vertical scrolling to work)

Here's my mouse config from xorg.conf. (ubuntu)

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Here's how SuSE configured my mouse:
> 
Section "InputDevice"
  Driver       "synaptics"
  Identifier   "Mouse[1]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Emulate3Buttons" "on"
  Option       "InputFashion" "Mouse"
  Option       "Name" "Synaptics;Touchpad"
  Option       "Protocol" "explorerps/2"
  Option       "SHMConfig" "on"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
  Driver       "mouse"
  Identifier   "Mouse[3]"
  Option       "Buttons" "5"
  Option       "Device" "/dev/input/mice"
  Option       "Name" "ImPS/2 Generic Wheel Mouse"
  Option       "Protocol" "explorerps/2"
  Option       "Vendor" "Sysp"
  Option       "ZAxisMapping" "4 5"
EndSection


I've tried comparing and adjusting, but either I get the same result I have now, no scrolling, or the mouse won't work at all.

I really need help with this, going on vacation in a couple of dayts, really need it fixed by then, there's no internet where im going. Thanks for helping out!

---

### Post by stiankarlsen on 2006-06-25
Suddenly got it working by changing it like this:

> Section "InputDevice"
Identifier "Configured Mouse"
Driver "synaptics" //not mouse
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "SynPS/2" // not ExplorerPS/2
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

both vertical and horizontal scrolling is working, as well as double tapping and drag'n drop.

---

