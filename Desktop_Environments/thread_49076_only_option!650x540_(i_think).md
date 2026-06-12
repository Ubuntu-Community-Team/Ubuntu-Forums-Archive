---
title: "only option!650x540 (i think)"
date: 2005-07-14
forum: Desktop Environments
---

### Post by wingdom on 2005-07-14
i just installed it, and i only get  one screen resolution option, i believe it is 650x540, the screen im using is best at 1024x768, its sooo annoying! how can i fix this?

---

### Post by TheOtherShoe on 2005-07-15
Can you please post your xorg.conf file? You will find it at /etc/X11/xorg.conf 

There should be a stanza in the "Screen" section that says,

```
SubSection "Display"
    Depth 24
    Modes "1024x768"
EndSubSection
```
or something like that, possibly having a different value for Depth.

If the stanza you need is there then you should be able to switch to that resolution by opening System > Preferences > Screen Resolution.

---

### Post by wingdom on 2005-07-15
Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"ATI Technologies, Inc. 3D Rage LT Pro (AGP)"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage LT Pro (AGP)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x1508" "696x696" "640x640" "640x480" "632x632" "544x544" "504x504" "328x328"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x1508" "696x696" "640x640" "640x480" "632x632" "544x544" "504x504" "328x328"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x1508" "696x696" "640x640" "640x480" "632x632" "544x544" "504x504" "328x328"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x1508" "696x696" "640x640" "640x480" "632x632" "544x544" "504x504" "328x328"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x1508" "696x696" "640x640" "640x480" "632x632" "544x544" "504x504" "328x328"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x1508" "696x696" "640x640" "640x480" "632x632" "544x544" "504x504" "328x328"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection





there it is

---

### Post by wingdom on 2005-07-15
bump

---

### Post by maruchan on 2005-07-15
wingdom, please post your system specs, esp. video card make & model, and monitor make & model.

There is a way to fix this problem, don't worry.  :wink:

---

### Post by wingdom on 2005-07-15
the monitor is a flatpanel Gateway fpd 1500 and the video card is an ATI rage LT pro

---

### Post by maruchan on 2005-07-15
Thanks for posting your specs. I googled your monitor and found this in someone else's xorg.conf:

> 
Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Gateway FPD1500"
DisplaySize 300 230
HorizSync 30.0 - 61.0
VertRefresh 56.0 - 75.0
Option "dpms"
EndSection

Here is their "screen" section:

> 
Section "Screen"
Identifier "Screen0"
Device "Videocard0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Make a backup of your xorg.conf file and swap in the sections above, just for kicks and giggles...then restart. See if you can change your screen res. The trick for the monitor is having the correct display frequencies listed in your xorg.conf.

As for your video card, you may want to look in the HOWTO section for tips on ATI cards. Also, do a forum search for your card's model number to see what comes up.

---

### Post by wingdom on 2005-07-15
thanks 4 the help so far, but im still lost as to where all the files r that i need to change, how to change them, and what exactly im changing them to

bump

---

### Post by wingdom on 2005-07-15
ggrrrrr, nvm about my previous post, i found it, but i cant type anything, delete anything, or do anything at all to that file, help! plzzzzz, this is getting really annoying

bump

---

### Post by maruchan on 2005-07-15
At the Ubuntu desktop, type:

Alt+F2

Then type:

gksudo gedit /etc/X11/xorg.conf

It will ask for your system password. Type that in and you're good.

This way you should be able to edit the file and make changes. DON'T forget to save a backup copy (like xorg.conf.backup) before you make changes.

---

### Post by wingdom on 2005-07-15
i did that, and it didnt ask me 4 my password, and all i got was a blank text doc.

---

