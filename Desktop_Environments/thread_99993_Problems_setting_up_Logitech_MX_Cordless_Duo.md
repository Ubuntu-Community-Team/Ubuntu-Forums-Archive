---
title: "Problems setting up Logitech MX Cordless Duo"
date: 2005-12-06
forum: Desktop Environments
---

### Post by thekidder on 2005-12-06
I'm following the directions [here]("http://docs.tenshu.net/Logitech-MX-Duo-mini-HOWTO/index.html") to try to get the extra buttons on my Keyboard and mouse working, and the X Server won't start. The error I get is: 
```
(EE) LogitechMX700Mouse: cannot open input device
No core pointer

Fatal server error:
failed to initialize core devices
```
My xorg.conf looks like this:

```
Section "InputDevice"
	Identifier      "LogitechEliteKeyboard"
	Driver          "keyboard"
	Option          "CoreKeyboard"
	Option          "XkbRules"      "xorg"
	Option          "XkbModel"      "logiinkseusb"
	Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
	Identifier      "LogitechMX700Mouse"
	Driver          "mouse"
	Option          "CorePointer"
	Option          "Dev Name"              "Logitech USB Receiver"
	Option          "Dev Phys"              "usb-*/input1"
	Option          "Device"                "/dev/input/mice"
	Option          "Protocol"              "evdev"
	Option          "ZAxisMapping"          "9 10"
	Option          "Buttons"               "10"
	Option          "Resolution"            "800"
	Option          "Emulate3Buttons"       "no"
EndSection

...

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"LogitechEliteKeyboard"
	InputDevice	"LogitechMX700Mouse"
EndSection
```

---

