---
title: "Monitor Refresh rate"
date: 2006-05-02
forum: Desktop Environments
---

### Post by Jungingen on 2006-05-02
I'm using KM777DT monitor with resolution 1024*768 and refresh rate is 75, but hardware supports 85 (on windows) . I know i need to do something with configs, i found this info about my monitor:

CRT  	Size  	17" (16" Diagonal Viewable Area)
	Dot Pitch 	0.25mm
	Type 	True Flat Tube
Display 	Resolution 	1280 x 1024
	H-Freq. 	30 KHz ~ 72 KHz
	V-Freq. 	50 Hz ~ 160 Hz
	Dot Rate 	110 MHz
User Control 	Manual Control 	Power, OSD, Select (+,-), Adjust (+,-),Brightness, Contrast
	OSD Control 	Contrast, Brightness, H/V position, H/V size, Pincushion, Pinbalance, Trapezoid, Parallelogram, Color Temperature (9300,6500,User),Rotation, Zoom, Moire, Degauss, Recall, Language, OSD Move
Power Consumption 	  	130W Max.
Input Connector 	  	Analog R.G.B. 15 Pin D-sub
Regulations 	  	UL, CSA, DHHS, TUV/GS, CE, FCC-B, MPR-II
Dimension (WxHxD) 	  	414 x 410 x 458 mm
Weight 	  	16.4 Kg




but i don't know what i need to write in config file. Can anybody help me?

---

### Post by Sendervictorius on 2006-05-02
This link should help:
[https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28xorg.conf%29](https://wiki.ubuntu.com/FixVideoResolutionHowto?highlight=%28xorg.conf%29)

Its written for Hoary, but should be the same for breezy. You want the section titled:
"Undetected Monitor Specs"

---

