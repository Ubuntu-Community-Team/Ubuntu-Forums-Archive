---
title: "compiz problems - numerous"
date: 2009-03-30
forum: Desktop Environments
---

### Post by veganbikepunk on 2009-03-30
Here's all the relevant information I can think to give

```
paxana@compy:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
 Driver in use:         fglrx
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect fglrx driver version in use. 


```

```
paxana@compy:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: glXCreateContext failed
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

```

# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "AIGLX" "on"
	Option	    "IgnoreABI" "true"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105+inet"
	Option	    "XkbLayout" "us"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "Enable"
EndSection

Section "ServerFlags"
Option "IgnoreABI" "True"
EndSection
```

---

