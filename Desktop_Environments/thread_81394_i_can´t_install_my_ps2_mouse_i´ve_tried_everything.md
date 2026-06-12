---
title: "i can´t install my ps/2 mouse i´ve tried everything"
date: 2005-10-24
forum: Desktop Environments
---

### Post by mxyzptlk on 2005-10-24
i did this 

cat /proc/bus/ps2/devices

cat /dev/input/mice


  Section "InputDevice"
   Identifier  "Mouse0"
   Driver      "mouse"
   Option      "Protocol" "ps/2"
   Option      "Device" "/dev/misc/psaux"
   Option      "Emulate3Buttons" "true"
EndSection

and nothing happens

please help me

---

### Post by Xian on 2005-10-25
What do the settings in your /etc/X11/xorg.conf file look like?
Should be similar (but not exactly) like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
```

---

