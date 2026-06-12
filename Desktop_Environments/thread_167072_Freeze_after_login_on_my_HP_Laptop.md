---
title: "Freeze after login on my HP Laptop"
date: 2006-04-27
forum: Desktop Environments
---

### Post by kyle_charest on 2006-04-27
i have a similar problem with my laptop. I installed kubuntu on my computer, and it didnt work. i didnt know to update the KDE and X11 for it to have a GUI. anyways i tried kubuntu 6, and it worked the first time, after a reboot it wouldnt work. So i have decided to stick with breeze. the thing gives my a promt, no GUI. i booted up in recovery, and used aptitude to update everything (KDE andX11) and installed the stuff, and the thing is that it freezes after the login. someone pleasee help me i tried changing the initdefault using vim but the "id:2:initdefault" was at 2, and i was reading something that said if it is at 5 , then change it to 3. i just left it alone. i am a noob :( ...

Oh and my specs
_________________________
HP Pavilion ze2113us Laptop
Mobile AMD Sempron 2800+
1.87 GB of RAM (after virtural memory)
ATI RADEON XPRESS 200M
Seagate 60GB 4200RPM

---

### Post by louis_nichols on 2006-04-28
Well... I ran KDE (under [slax]("http://slax.linux-live.org/")) on a HP laptop with a very similar configuration and worked flawlessly.

I wouldn't go as far as to modify initdefault. The 2 vs 5 thing is just because other Linux distros run in default runlevel 5 (RedHat, Fedora Core etc.), but Ubuntu runs in 2 (runlevels are just a matter of a list of software to start - not that important for the average home user). Your problem is obviously somewhere else.

So what I'm suggesting is that you set initdefault back to id:2:initdefault. Then, try to login again. If it doesn't work, post here the exact error you are getting, so we know where to start troubleshooting this.

---

### Post by kyle_charest on 2006-04-29
Well thanks for the reply. My problem with everything back to normal is when i start up, the consol loads and everything. after i put in my password and press enter it sometimes makes it to the sound, and when it does my HDD activity light goes off, and a second later the sound freezes, like it is laging. so i leave it alone for about 5 min to see if it will start working again, and it is still playing the skipping sound. i dont know what to do... i know it is not the dvd because my friend installed it on his Compaq R3000.Any sugguestions?

---

### Post by louis_nichols on 2006-04-30
I don't know what might be wrong. Please post here the contents of /var/log/Xorg.0.log. it might give us a clue.

---

### Post by kyle_charest on 2006-05-03
here it is...

i couldnt figure out how to get it on here, and it was too big to put it as an attachment, so i renamed it as a .zip, it still is a .txt file, so just change the extension... thanks

---

### Post by louis_nichols on 2006-05-03
[QUOTE=kyle_charest]here it is...

i couldnt figure out how to get it on here, and it was too big to put it as an attachment, so i renamed it as a .zip, it still is a .txt file, so just change the extension... thanks[/QUOTE]


Ok. I think I'm starting to get a clue of what's happening. For comparison, my Xorg.0.log file has only 22kB.

I'm guessing you have an ATI mobility radeon 200M video card and haven't installed the ATI proprietary drivers yet... I should have asked you to also post your xorg.conf file here...

I was going to recommend a more complicated solution, but the easiest thing you should try, first, is to simply install the proprietary ATI drivers. So, here's what you should do:

1. Make sure all repositories are activated.

```
sudo gedit /etc/apt/sources.list
```

Remove the character **#** in front of all lines that start with **deb** or **deb-src**. If you have over there a section that refers to a cdrom, comment out everything related to that by putting a # at the beginning of each of those lines.

2. Install drivers```
sudo apt-get update && sudo apt-get install xorg-driver-fglrx
```

After this, things should work. Good Luck! And please let me know how this turns out.

EDIT: Strike the guessing over there, about the video chipset. it says right there in the log file: ```
(II) Primary Device is: PCI 01:05:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon Xpress 200M (RS480)".
(--) Chipset ATI RADEON XPRESS 200M Series found
```
But I didn't think to look. #-o

---

### Post by kyle_charest on 2006-05-05
Well after trying everything you said, nothing changed. during normal startup i pressed <alt><ctrl><F8> to get to the non gui screen and switched back to F7 and input my password, and imediately switched back to F8 and i heard the startup sound, and when i went to the KDE desktop i saw the outline of the taskbar atleast! 

but sudo gedit didnt work so i put "vim /etc/apt/sources.list" and edited it that way, and i was in recovery mode so sudo didnt work either, idk f i needed it since my username was root@kubuntu:

Oh and i noticed that during startup, when it is starting the "Starting ISDN services" it fails, it says "Neither /dev/isndinfo nor /dev/isnd/isndinfo exist" i dont know if that could be the problem, if so idk how o fix it. thanks for your help though. 


here is the contents of my xorg.conf file


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg-dbg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg-dbg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg-dbg

Section "Files"
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

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Driver		"ati"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by louis_nichols on 2006-05-05
man, this is weird! Here's what I want you to try:

1. first, make a backup of your current xorg.conf, so you have something to back to if things go wrong. :) 

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

2. Open xorg.conf for editing. I like nano instead of vi, cuz it's more intuitive:
```
sudo nano /etc/X11/xorg/conf
```

3. Change the following:

here ```
Load "ddc"
Load "dri"
Load "extmod"
```

Comment out dri"

```
Load "ddc"
#Load "dri"
Load "extmod"
```

here:```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
Driver "ati"
BusID "PCI:1:5:0"
EndSection
```

change driver to vesa and comment out busID

```
Section "Device"
Identifier "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
Driver "vesa"
# BusID "PCI:1:5:0"
EndSection
```

comment out all this part ```
# Section "DRI"
# Mode 0666
# EndSection
```

4. Try to login again. Fingers crossed!

it's the vesa driver that I used to solve a surprisingly similar problem on a toshiba laptop.

---

### Post by kyle_charest on 2006-05-05
i was just wondering why you think it is a display problem?

---

### Post by louis_nichols on 2006-05-05
EDIT: the post wasn't meant to be so short, I just mistakenly clicked save instead of go advanced

because your Xorg.0.log file says it has trouble with dri.```
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
```

It has a couple of hundred entries like that. Also, because I ran into similar problems with a toshiba laptop using an ATI Mobility radeon 200M.

Of course, I may be wrong, in which case I'm terribly sorry.

---

### Post by kyle_charest on 2006-05-05
oh well it worked, but the screen is very big, do i now need to install the proper drivers?

---

### Post by louis_nichols on 2006-05-05
[QUOTE=kyle_charest]oh well it worked, but the screen is very big, do i now need to install the proper drivers?[/QUOTE]

glad to hear we've gotten somewhere, finally :) the big screen thing is a resolution issue. did you try adjusting the resolution and refresh rate?

about the driver... I really don't know. It was supposed to just work the first time, so that puzzles me. The toshiba laptop I was talking about has a mobility radeon xpress 200m which is supposedly not even supported by the 
ATI driver for Linux, but worked flawlessly after installing it.

I would try replacing vesa with ati in the driver section, but keeping dri commented out. If it doesn't work, we're gonna need to take a look at the generated /var/log/Xorg.0.log again...

---

### Post by kyle_charest on 2006-05-05
ok well i am leaving for 2 days, and i wont have internet, but i will let you know when i get back! and thanks again for helping me!! :) the refresh is at its max, which is sixty something rather then 72, and the res is at 1024x786... So i dont know what to do there. When i was configuring things i couldnt see thebottom of the window, so i had to tab to be in admin mode on the crtl pannel...thats why i was thinking it is too big. Is there a way to change it and trick it to making it into 1280x* so everything is smaller?? thanks

---

### Post by louis_nichols on 2006-05-05
I know what you're talking about, cause I've seen it too, but for me it always dissapeared after installing the proprietary drivers.

someone recommended me, in a fairly similar situation, to use xvidtune > use xvidtune from the command line, correct the positioning of the screen, then use the modeline that xvidtune prints out in the terminal in your xorg. conf file. Like this:

Section "Monitor"
Identifier "SyncMaster"
HorizSync 30.0 - 65.0
VertRefresh 50.0 - 75.0
ModeLine "1280x1024" 108.0 1280 1356 1468 1688 1024 1025 1028 1066 + hsync +vsync
Option "DPMS" "true"
EndSection

---

### Post by richbarna on 2006-05-05
I have seen this same problem while installing Ubuntu on laptops for friends.
On some i changed the xorg.conf file by changing the "ati" for "vesa", on others i did the ubuntu "server" install and then apt-get the kde desktop afterwards.
I'm a Newbie too and i don't know the ins and outs of why this solved the problem but it seems to work.

---

