---
title: "Second display gone"
date: 2009-03-17
forum: General Help
---

### Post by shannondoko on 2009-03-17
Greetings!

(Below might or might not have anything to do with it, but just in case it does I'm letting you know. )
Last night I installed gnome do 0.8.1 and Shiki Colors (using the script)
Everything worked perfectly. That night I turned off my computer, then the next morning my second display was gone.

I have an alienware area-51 m5750 with the ati x1800 proprietary drivers are installed. 

Everything worked fine before, now it's like the second monitor doesn't even exist. 

I did some tinkering using the ati commants, and it completely broke my xorg, to the point where the login screen wouldn't show up. below is the code of the broken xorg.conf 
```

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "Default Screen" 0 0
	Screen         "aticonfig-Screen[0]-1" Above "Default Screen"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
	DefaultDepth     24
	SubSection "Display"
		Virtual   1680 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	Monitor    "aticonfig-Monitor[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```
I had to use the boot cd to change my xorg back. 

Is there anyone out there with magic ubuntu powers who could help me??

---

