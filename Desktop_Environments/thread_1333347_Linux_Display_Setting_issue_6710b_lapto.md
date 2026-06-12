---
title: "Linux Display Setting issue 6710b lapto"
date: 2009-11-21
forum: Desktop Environments
---

### Post by masoodasif on 2009-11-21
Dear Linux Masters 

i have just installed the REDHAT Linux AS4 on my virtual machine. My host Operating system is windows 7 and my laptop model is Compaq 6710b but unfortunately i configured the wrong display at the first time settings screen and when my Linux machine boots up i canâ€™t see anything because it is so much Blurry Screen. i am sending you the copy of my xorg.conf file could anyone please tell me that what will be the settings for my laptop and your kind quick response is highly appreciable 
thanks
Regards
Masood Asif
 Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Unknown monitor"
	HorizSync    31.5 - 37.9
	VertRefresh  50.0 - 70.0
	Option	    "dpms"
EndSection

Section "Device"
	Identifier  "Videocard0"
	Driver      "s3"
	VendorName  "Videocard vendor"
	BoardName   "S3 Trio64 (generic)"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Videocard0"
	Monitor    "Monitor0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     16
		Modes    "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group        0
	Mode         0666
EndSection

---

### Post by masoodasif on 2009-11-21
can any one help me to change the settings because it is really very urgent for me i need to prepare one presentation for linux and i am stuck at first stage :-(

Regards
masood

---

### Post by masoodasif on 2009-11-21
this is the xorg.conf file


Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Unknown monitor"
HorizSync 31.5 - 37.9
VertRefresh 50.0 - 70.0
Option	 "dpms"
EndSection

Section "Device"
Identifier "Videocard0"
Driver "s3"
VendorName "Videocard vendor"
BoardName "S3 Trio64 (generic)"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 16
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
Modes "800x600" "640x480"
EndSubSection
EndSection

Section "DRI"
Group 0
Mode 0666
EndSection

---

