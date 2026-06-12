---
title: "xorg will only run at 640x480"
date: 2005-04-25
forum: Desktop Environments
---

### Post by cannibalbob on 2005-04-25
I had it running great at 1024x768.  Then one day i booted into windows, and when i started ubuntu again, it only runs at 640x480.  xorg.conf is exactly the same, with the screen section set to 24 bit and 1024x768.  changing the color depth makes no difference.  any ideas?

---

### Post by nad on 2005-04-25
Edit your boot line at the grub startup selection menu to include the parameter: vga=792

To edit these selections, use the e key after you have highlighted the entry you wish to edit, and the arrow and backspace keys to manipulate the cursor. A short help is on the screen.

---

### Post by cannibalbob on 2005-04-25
no difference

---

### Post by cannibalbob on 2005-04-25
heres my xorg.conf:

> Section "Files"
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
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"6 7"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Driver		"ati"
	BusID		"PCI:3:0:0" 
EndSection

Section "Monitor"
	Identifier	"ViewSonic GS"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9200 (RV280)"
	Monitor		"ViewSonic GS"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
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


---

### Post by tread on 2005-04-25
Try recreating it.

I don't know how to do this in ubuntu (dint have to yet) but heres my guess:
Backup the current xorg file, 
then fire up synaptic, find the xorg server package and reconfigure it. (I dont remember the exact location of that option, and I am on a Solaris machine right now so I cant check)

Maybe that will get you back onto 1024x768.

---

### Post by tread on 2005-04-25
Before that, try cycling through resolutions? I think thats ctrl-alt-plus.

Ubuntu should also have a screen resolution option in system->preferences I think. Make sure that is set to 1024x768.

---

### Post by nad on 2005-04-25
I have an idea. I play around with multi-monitor, multi-card setups. Problems initializing the cards can sometimes be solved by moving to another address. One point of doing this is to try for a different interupt. But it always has the effect of uninitializing the card as power has been removed for some 10's of seconds.

Modern boxes are always powered. Changing the address of an agp card is not possible without modifying the bios, however, if it is removed count to 30 and replaced it will need to be reinitialized at startup. Please post any results.

Before the card is removed, unplug the box and hold the power button in for a few moments to drain all the capacitors on the board. With the plug out of the box, you will be surprised to see the cpu fan and possibly other components react as they help to drain the system.

Just a thought.

---

### Post by alastair on 2005-04-25
If you don't get anywhere, post your X log :

/var/log/Xorg.0.log

---

### Post by RuKK on 2005-04-25
I believe that your problem is that under your "Monitor" section, you dont have HorizSync and VertRefresh specified. Here is a example of mine. Google for your monitor's correct specifications and plug them in there. Then restart X by logging out and ctrl+backspace  or restarting the computer.

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	29-75
	VertRefresh	50-140
EndSection


Hope this helps,

James

---

### Post by cannibalbob on 2005-04-25
Not specifying the vertrefresh and horizsync turned out to be the problem.  thanks  :smile:

---

### Post by stamy on 2005-04-26
I has the same problem, i dont test with the range line in xorg.conf

But, when i powered the box it is in 640*480, and then after a reboot it cames back to 1024*768.
Oh i forgot, it was probably because the monitor was shutoff when i start the PC, so xorg cannot detect it correctly and choose a standart resolution: 640*480.

So i guess, i have two solutions, put the refresh values in the file, or start with the monitor powered on before the rest of the box :-)

Thank's for the help.

---

