---
title: "Screen Resolution"
date: 2005-09-10
forum: Desktop Environments
---

### Post by johnv on 2005-09-10
Hi Guys,
I am an absolute newbie when it comes to Linux.  This is the 1st distro that I am like and so far I like it, I tried Libranet but this is better.

I have installed Ubuntu on an older pc to act as a file/print server.  Now I just installed it and ran the updates.  My problem is screen resolution.  I cannot change the screen resolution at all.  It's stuck at 680x480 & its way to huge.  I went to change the resolution but the 680x480 is the only option.  

During the setup I selected 680x480, 800x600 & 1024x768.  Any help would be greatly appreciated.

I am a complete newbie when it comes to Linux/Ubuntu.  I know Windows but that doesn't help me here.

Thanks in advance for your help guys!

---

### Post by mlomker on 2005-09-10
Screen resolution and driver are configured in /etc/X11/xorg.conf.  First you're going to have to figure out what card is in the machine and what driver is being used.  Look in the aforementioned file for a Driver line under Section "Device" and that'll tell you what driver is in use.  The **lspci** command will give you a list of the PCI devices in your machine and perhaps a clue as to what driver should be used...from there it's time to search the forums and Google for an answer.

I'll warn you that linux has a steep learning curve.  If you want low-stress than stick to Windows.  If you are a nerd or perhaps even work in the computer field, then *welcome!*

---

### Post by Fridericus on 2005-09-10
I had a similar problem, my screen resolution was stuck at 1024x768, I could not go any higher only lower (800, 640 etc), I wanted to use 1152x 864 (I had like you chosen that resolution during the installation process) but it was not in the Screen Resolution list.

This is how I made it work.
I edited my xorg.conf file 

```
gedit /etc/X11/xorg.conf
``` 

Added the resolution under **Section "Screen"** for all colour depths.

Then under **Section "Monitor"** I put my monitors Horizontal Sync and its Vertical Refresh rate (these should be listed in the manual you got with your monitor, you can try and Google for them also "X Y specifications"  (X=Brand Y=Model))

For my DELL D1226H the HorizSync and VertRefresh numbers are 30-95 kHz and 50-160 Hz

```
Section "Monitor"
Identifier"Generic Monitor"
Option"DPMS"
HorizSync30-95
VertRefresh50-160
EndSection
``` 

Now I am able to select 1152x864.

[COLOR=Red]Perhaps someone should verify what I just wrote before you give it a try.[/COLOR]

---

### Post by Waqas on 2005-09-11
May I know what is "DPMS" on Option?

My monitor is a Venus 17", unluckily theres nothing on Google about my monitor. The manual is lost along the box when I moved to a new house years ago. So Im not very sure what to insert on the xorg.conf. Can someone still help me??

---

### Post by johnv on 2005-09-11
Thanks guys,
I tried what you said & it worked.  I am used to windows but I want to try linux.  I am up for the challenge.  Don't worry, I will be back to ask more questions later.

Thanks again!
 :grin:

---

### Post by mlomker on 2005-09-12
[QUOTE=Waqas]May I know what is "DPMS" on Option?
[/QUOTE]

I believe it has to do with power management.  The relevant lines are the horizontal and vertical sync rates.  If you want more help then post a copy of your /etc/X11/xorg.conf file and explain what you are trying to do (what resolution are you trying to get?).

---

### Post by raijin2k on 2005-09-12
hi all im also having problem with my screen resolution.my monitor is aoc 5en .tried some setting on this forums but wont work.i just wanna get a 1024x768 resolution.

my xorg.conf

Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
	Load	"i2c"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option		"NoLogo"
EndSection

Section "Monitor"
	Identifier	"5En"
	Option		"DPMS"
	HorizSync30-54
	VertRefresh50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"5En"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"800x600" "640x480"
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

im a newbie to linux!!!

---

### Post by KenLazlo on 2005-09-13
make shure the values HorizSync and VertRefresh  are correct for your monitor

Then change the Modes-Lines to 

Modes "1024x768" "800x600" "640x480"

Restart X   (e.g. Alt+Ctrl+Backspace)

---

### Post by mlomker on 2005-09-13
I don't have an nvidia, but I've heard elsewhere that the included driver is only 2D and doesn't have the nice features.  Go into Synaptic and install the **nvidia-glx** package.

The instructions then say to use the **sudo nvidia-glx-config enable** command in a terminal prompt.

---

### Post by raijin2k on 2005-09-13
thanks guys..managed to get it to work.

---

### Post by kenweill on 2007-09-03
> **raijin2k said:**
> thanks guys..managed to get it to work.

how? i've had the same problem with NVIDIA GeForce FX5500 with AOC 5en Monitor.
It works alright with other monitors but with AOC monitor, it wont. It just stops on blank screen with all the lights on the monitor to blink.. on and off..

In the monitor manual, it states that
Horiz Freq is 30-56
Vertical Freq is 50-120

I did put that in the xorg.conf to no avail... The only driver to make it work with the monitor is NV and VESA drivers only.. NVIDIA doesnt work, with AOC 5en..

---

### Post by surfer57 on 2007-09-03
Restart X (e.g. Alt+Ctrl+Backspace) oh what masterful controls....that did the trick for me....I have been starting out in the 800 X 600 since my last upgrade....the restart of X cleared it right up....thanks for your help!!! Ubu N tu ROCKS!!!!

---

### Post by kenweill on 2007-09-20
> **surfer57 said:**
> Restart X (e.g. Alt+Ctrl+Backspace) oh what masterful controls....that did the trick for me....I have been starting out in the 800 X 600 since my last upgrade....the restart of X cleared it right up....thanks for your help!!! Ubu N tu ROCKS!!!!

Thats what im talking man. Im stuck in 800X600 resolution.
It wont work with 1024X768 resolution. 800X600 is useless. Some of the apps dont fit in my screen with that kind of resolution and its unusable.

---

### Post by Metaphor on 2007-09-27
moved to beginner section sorry

---

