---
title: "Yet another plea for help in playing WoW with wine"
date: 2006-09-30
forum: Gaming &amp; Leisure
---

### Post by hellocharlie on 2006-09-30
I've been butting my head against this and other issues related to WoW in wine for months.

Thanks to questions already posted and answered, I've managed to get pretty far.

Everything works beautifully until I've entered the game world. At this point, my character is invisible, as is her portrait in the top left corner. The minimap works well, tracking all movement of my ghosted character. No other player characters are visible, PCs or NPCs alike, just the environment.

Sound seems to work as expected, for both music and effects.
At roughly 3 seconds of this, the game freezes (yet music continues). I can't seem to get a system response after this, unless I forcibly power down.

I'm truly sorry if I've overlooked postings relative to this issue and if anyone has a link to share, I would greatly appreciate it. Otherwise, any advice would also be similarly celebrated and praised.

I am running Dapper on a system with a Pentium D 930 on kernel 2.6.15-27-686, with fglrx driving my ATI X600SE. My xorg.conf file looks like this:

> Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
EndSection

Section "Monitor"
	Identifier	"DELL 1907FP"
	Option		"DPMS"
	HorizSync	31-83
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
	Monitor		"DELL 1907FP"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by Ferrat on 2006-09-30
What version of Wine are you using and what videodrivers?

---

### Post by hellocharlie on 2006-09-30
My wine installation is 0.9.20 and video drivers are fglrx (from xorg-driver-fglrx 7.0.0-8.25.18+2.6.15.11-5).

Sorry for not mentioning that before.

---

### Post by Ferrat on 2006-09-30
Ok try istalling wine 0.9.22 (latest) and the lastest ATi driver that might help and the latest wine has alot of wow fixes my wow runs (without any patches) and I got good FPS and no problems =)

---

### Post by hellocharlie on 2006-09-30
With doubt in my mind I ventured to upgrade wine.

Lo and behold!

A mere difference of 0.0.02 has repaired all of my Warcrafting woes.

I did find that in Crossover Office's new beta that the minimap works indoors as opposed its loss when simply running in wine. Whodathunk?

Thanks, kindly for your help.

---

### Post by Ferrat on 2006-10-01
From what I've heard Crossover is acctually really good but the minimap IMHO is a small problem, but worth to keep an eye on crossover =)

---

### Post by hellocharlie on 2006-10-01
Alas and alack, friends. The victory cheer was a bit premature. It would seem that the very same issue as earlier described seems to have reappeared.

I've installed no other software, made no configuration changes or anything of the sorts since my 30 minute romp through Ironforge last night.

Now, with the Crossover beta on board, I can confirm that both pure wine and Crossover fail in the same manner.

Does anyone have any additional suggestions?

Cheers!

---

### Post by Ferrat on 2006-10-01
Yes check your cooling on the comp sound like it can be overheating

---

### Post by hellocharlie on 2006-10-01
I could be wrong, but I doubt that's the issue. Everything is well ventilated... and though I know this is a fallacy... (and is worsened by the fact that I don't have a temperature guage) it doesn't give off any heat to the touch. In addition, everything runs properly (and on the highest settings) from a Windows partition (EEK!).

Though, (and I'm retisent to admit this) my thought lies in blame to the card as well as it's not directly supported by fglrx... and I doubt it ever will be.

When my ducks are all lined up properly, I may purchase an NVIDIA... as ATI has ever given me grief in driver issues.

Again, you may be right about the heat... but there don't seem to be any other indicators that it's an issue.

Thanks, kindly for the advice.

---

