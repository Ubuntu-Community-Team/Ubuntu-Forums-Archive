---
title: "Odd Doom3 problem, mouse and resolution issue"
date: 2008-01-12
forum: Gaming &amp; Leisure
---

### Post by Huzudra on 2008-01-12
alright, i got doom3 installed here much to my delight.  it launched and ran, the first thing i did was change to my favorite resolution of 1024x768. i closed and re-launched it.  the ingame mouse cursor is drawn, but does not move....i cannot click on a darned thing!  this issue was not present at the default resolution of 640x480...im not sure whats going on to cause this problem.  the only way i can get out is to ctrl alt backspace and restart X.:(


1.6 E2140 @ 2.13
2GB DDR2800
250GB HDD
Foxconn board with the 965GZ chipset
XFX 7600GT
Gateway EV700 Monitor
Generic 5 button USB optical mouse
Generic PS2 Keyboard

---

### Post by tgalati4 on 2008-01-13
Does the mouse work at 800 by 600?

You have an onboard Intel 965GZ chipset.  This might be a stretch, but did you try turning off the on-board graphics card?  Perhaps the hardware cursor/software cursor is getting confused because of the on-board graphics card.  I assume that you are using the 7600 card to drive your display.

I also assumed that you used envy to grab the latest nVidia drivers for your 7600 card.

---

### Post by Huzudra on 2008-01-13
i never tried 800x600....i cant set it to anything since i cant get the mouse to work and for some reason i cant find the cfg file to edit the res back to something else.  i'll check in bios about the onboard being enabled or disabled.  my nvidia driver is version 100.14.19. 

yes, the 7600GT is driving the display.  and now i do remember changing a bios setting to get the screen onto the 7600GT, but im not sure if that disabled the onboard, i'll check into that in the morning.


thanks for the fast reply, you'll have to be patient with me...ive been out of the linux loop for a while and was never that deep into it to begin with.

---

### Post by Huzudra on 2008-01-13
alright, im pretty sure i have the onboard disabled now (this foxconn phoenix BIOS is a little alien to me).  the problem persists.  if i ctrl alt del the menu comes over the game but the mouse is still not present.  if i press shift f7 i can see the desktop mouse cursor in the upper lefthand corner of the screen. shift f7 is what activates the water cursor effect on the compiz on this setup here.

:confused:

can someone atleast tell me how to reset the resolution without reinstalling?

---

### Post by tgalati4 on 2008-01-13
Turn off compiz.

---

### Post by Huzudra on 2008-01-13
> **tgalati4 said:**
> Turn off compiz.

i'll try that


success!  thanks, i didnt think that compiz would screw with doom3...goes to show what i know.

---

### Post by Huzudra on 2008-01-13
alright, now when i change the res to higher than 1024x768 (im using doom3 as a relative benchmark to compare this computer to mine) the screen is not centered anymore...it feels like when you set an LCD to the wrong resolution and part of the screen is off the screen if you know what i mean, but this is a CRT display.  whats going on with this?

---

### Post by tgalati4 on 2008-01-15
Changing resolution will change the scan rates.  You will need to readjust your CRT using the front panel controls to recenter and maximize the screen area.  It's also possible that you don't have the proper modelines or scan rates in your xorg.conf file.

---

### Post by Huzudra on 2008-01-15
ection "Monitor"
	Identifier	"Failsafe Monitor"
	Vendorname	"Gateway"
	Modelname	"Gateway EV700"
	Horizsync	30.0-70.0
	Vertrefresh	50.0-120.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1400	1050
		Modes		"1024x768@75"	"1024x768@70"	"1024x768@85"	"1024x768@60"	"832x624@75"	"1024x768@43"	"800x600@60"	"1152x864@75"	"800x600@85"	"1280x960@60"	"800x600@75"	"1280x1024@60"	"800x600@72"	"1400x1050@60"	"800x600@56"	"640x480@85"	"640x480@75"	"640x480@72"	"640x480@60"
	EndSubSection



that looks like its correct, no?  moving the screen around with the monitors controls or resizing with the monitors controls only makes whats being drawn ON SCREEN move around, the problem is that about 1/2 is being drawn off screen and all i can see is the upper right corner.:confused:

---

### Post by Huzudra on 2008-01-19
bump about the resolution issue?

also UT2004 crashes with this in console when i try to set 1280x1024 res

cat@cat-linux:~$ '/home/cat/ut2004/ut2004' 
WARNING: ALC_EXT_capture is subject to change!
Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x1a5
  Serial number of failed request:  243
  Current serial number in output stream:  244
cat@cat-linux:~$ 


:confused:

---

