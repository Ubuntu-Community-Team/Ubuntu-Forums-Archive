---
title: "Only one mouse works"
date: 2006-01-03
forum: Desktop Environments
---

### Post by installer on 2006-01-03
Hello I have followed this [Wiki]("https://wiki.ubuntu.com/MX1000Mouse") to get my 12 button (usb) mouse working, but now my ordinary ps2 mouse no longer works any ideas? I need to have two connected/working.

here is part of my xorg.conf



```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection



Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Protocol"              "evdev"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb-*/input0"             
        Option          "Device"                "/dev/input/event1"           
        Option          "Buttons"               "12"
        Option          "ZAxisMapping"          "4 5 7 6"
 EndSection


Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option          "NoLogo"
        Option		"UseFBDev"		"true"
EndSection

```

Thanks.

---

### Post by Ocxic on 2006-01-03
could it be that you should be only using one mouse and using 2 confuses X

---

### Post by installer on 2006-01-03
[QUOTE=Ocxic]could it be that you should be only using one mouse and using 2 confuses X[/QUOTE]

No I don't think so because they will both work if I comment out this section but I loose the extra buttons

```
#Section "InputDevice"
       # Identifier      "Configured Mouse"
        #Driver          "mouse"
        #Option          "CorePointer"
        #Option          "Protocol"              "evdev"
        #Option          "Dev Name"              "Logitech USB Receiver"
        #Option          "Dev Phys"              "usb-*/input0"             
        #Option          "Device"                "/dev/input/event1"           
        #Option          "Buttons"               "12"
        #Option          "ZAxisMapping"          "4 5 7 6"
 #EndSection

```

The reason for the two mice is that when the usb mouse needs charging, I just pickup the other PS/2 mouse.

---

### Post by Ocxic on 2006-01-03
so I'm right, you can pnly have one DEVICE section for a mouse using 2 will confuse X, why do you need 2 mice anyway?

---

### Post by installer on 2006-01-03
[QUOTE=installer]

The reason for the two mice is that when the usb mouse needs charging, I just pickup the other PS/2 mouse.[/QUOTE]

:neutral:

---

