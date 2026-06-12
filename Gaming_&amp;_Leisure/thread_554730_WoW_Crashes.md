---
title: "WoW Crashes"
date: 2007-09-19
forum: Gaming &amp; Leisure
---

### Post by jmb272 on 2007-09-19
Before you begin thinking "i bet this noob hasn't even looked at the other wow crash topics", well, I HAVE, i've not found other posts which describe a crash as bad as this.

I've installed all the patches successfully, i then opened WoW.exe using  the command "wine WoW.exe".

I've read that using "wine WoW.exe -opengl" is better but it isn't for me, appending -opengl onto the end makes WoW run even slower, alot slower.

So anyway, i can get into WoW, i click on "Agree" but when i click on the second "Agree" button, Wow crashes, not just any crash, i cant ALT+Tab out or ALT+F4 it, i cannot escape the WoW window so i end up having to press the power button my PC.

Has anyone else had this problem?
Can someone help me resolve this please?

---

### Post by TidusBlade on 2007-09-19
I dunno much about WoW on wine but I used [this](http://www.wowwiki.com/Linux/Wine) guide, and I had problems before and now I dont have much ^_^
But Im also a n00b to linux :P So it probably wont work for you... good luck :D

---

### Post by ageilers on 2007-09-19
Go into your Wine config. You can do this from terminal with "winecfg". Add WOW.exe to applications list. Select it and change the drop down box to "XP". Dowload [[COLOR="DarkOrange"]mfc42.dll[/COLOR]]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc42") and copy it to "/home/<your user name here>/.wine.drive_c/windows/system32". Go to the libraries tab and add riched20.dll, riched32.dll, mfc42.dll. 
Hopefully this will help.

A good reference is:
[URL="http://appdb.winehq.org/appview.php?iVersionId=5606"]
[COLOR="DarkOrange"]http://appdb.winehq.org/appview.php?iVersionId=5606[/COLOR][/URL]

This one is for Gentoo, so some things are different. But still a good reference:

[[COLOR="DarkOrange"]http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine[/COLOR]]("http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine")

---

### Post by ageilers on 2007-09-19
Great link Tidus!

To get to your desktop after a WOW crash, you should be able to use Ctrl+Alt+D. I know it works in Kubuntu. Then kill WOW with whatever process manager is in Ubuntu.I believe you want System->Administration->System Monitor, then click the Processes tab. Look for WOW.exe and possibly wineserver.

---

### Post by TidusBlade on 2007-09-19
> **ageilers said:**
> Great link Tidus!
Thanx ^_^ I just hope it helps :P

---

### Post by jmb272 on 2007-09-19
> **ageilers said:**
> Go into your Wine config. You can do this from terminal with "winecfg". Add WOW.exe to applications list. Select it and change the drop down box to "XP". Dowload [[COLOR="DarkOrange"]mfc42.dll[/COLOR]]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc42") and copy it to "/home/<your user name here>/.wine.drive_c/windows/system32". Go to the libraries tab and add riched20.dll, riched32.dll, mfc42.dll. 
Hopefully this will help.

A good reference is:
[URL="http://appdb.winehq.org/appview.php?iVersionId=5606"]
[COLOR="DarkOrange"]http://appdb.winehq.org/appview.php?iVersionId=5606[/COLOR][/URL]

This one is for Gentoo, so some things are different. But still a good reference:

[[COLOR="DarkOrange"]http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine[/COLOR]]("http://gentoo-wiki.com/HOWTO_Install_and_update_World_Of_Warcraft_with_wine")


Thanks, it worked.

---

### Post by jmb272 on 2007-09-19
OOO, when i login my character doesn't appear and the WoW client crashes just like it did before.

---

### Post by ageilers on 2007-09-19
What is your hardware setup? ATI, Nvidia, or onboard video? What version of Ubuntu are you using?

---

### Post by jmb272 on 2007-09-19
using Ubuntu Christian Edition 3 (Ubuntu 7.04 Feisty).

My Graphics (copied from website).
manufacturer : ATI
type : ATI Radeon® Xpress 200M
memory : up to 128 MB 

1gb ram, 1.5ghz cpu.


I just logged on to wow now, my character didn't appear but i managed to rotate for a few seconds in the graveyard before it crashed.

---

### Post by jmb272 on 2007-09-19
Hmm, i logged on and my character appeared but then it crashed again. It crashes after about 8 seconds.

the only way i can get it to close without switching my comp off with the power button is with a perl script, an sh script & the AT command.

I coded a small perl script to find the PID number of the WoW process and kill it with "kill -s kill ID", i wrote a small bash script to run the perl script, then just before i open up WoW, i use the AT command to run the bash script in 1 minute, so if i log into WoW and it crashes, at least i wont have to switch off & on again.

---

### Post by ageilers on 2007-09-19
Did you try again with opengl?

```
wine WOW.exe -opengl
```

---

### Post by jmb272 on 2007-09-19
I'll try now thanks.

Just tried it, its still worse with -opengl than it is without.

---

### Post by ageilers on 2007-09-19
Was WOW working earlier on this PC? Can you post the contents of your /etc/X11/xorg.conf?

---

### Post by jmb272 on 2007-09-19
navn't played WoW on linux before, just installed it earlier.

**My xorg.conf**
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RC410 [Radeon Xpress 200M]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1280x768"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1280x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

---

### Post by NibbleG on 2007-09-20
I had WoW working before, i actually just moved to Ubuntu in the past few days, so yeah... i am pretty new, I followed several guides, and got Wine and WoW installed, updated.  For a long time it would open, log in, and crash, a few seconds in and a hard crash.  Then i finally got my ATi x300 to work, and everything was fine, except i couldn't change the video options in game... One guide, suggested temporarily running the game in D3D to make the changes, I had removed 

SET gxApi "opengl" 

and, yeah it crashed after i logged in and chose my character.  but after adding the line back in, i still crash.

I'll give you all the info you want, but i don't know how.... tell me how to find it and you shall receive.

Thanks in advance

Nibble G

---

