---
title: "Cant login anymore"
date: 2007-11-26
forum: Desktop Environments
---

### Post by elfstone2 on 2007-11-26
Hi, since yesterday i cant login into my kubuntu 7.10 anymore. I get the login screen, but no matter what user or Enviroment (Kde/Gnome/Failsafe) i use, i only get a flicker and go back to the loginscreen.
I tried to install the ati-drivers, but that didnt help either. Its a thinkpad with ATI X1300.
Any Ideas what can be wrong, or what i can try to fix it?

xorg.conf:
```
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
```

Xorg.0.log:

```
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) Open ACPI successful (/var/run/acpid.socket)
(II) APM registered successfully
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: ATI ATOMBIOS
(II) VESA(0): VESA VBE OEM Software Rev: 9.12
(II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) VESA(0): VESA VBE OEM Product: M54CSP
(II) VESA(0): VESA VBE OEM Product Rev: 01.00
(==) VESA(0): Write-combining range (0xd8000000,0x1000000)
(II) VESA(0): virtual address = 0xb69dc000,
	physical address = 0xd8000000, size = 16777216
(==) VESA(0): Default visual is TrueColor
(**) VESA(0): DPMS enabled
(==) RandR enabled
(EE) AIGLX: Screen 0 is not DRI capable
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```


Thx for help..

---

### Post by HJB on 2007-11-29
Can you login with Ctrl Alt and F4 for example?

---

