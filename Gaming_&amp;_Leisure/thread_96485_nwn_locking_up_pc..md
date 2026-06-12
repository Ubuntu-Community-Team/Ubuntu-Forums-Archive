---
title: "nwn locking up pc."
date: 2005-11-29
forum: Gaming &amp; Leisure
---

### Post by bb002 on 2005-11-29
I've installed NWN Platinum according to an "unofficial" method posted on the bioware forums and my install passes the md5sum test that also on the bioware forums. Only two files fail fixinstall.sh (didn't run it since the installer script manually fixed the file cases for me.) and the nwn file (which i manually edited to cd to the nwn directory and removed the nwn libs folder).

Now the problem arises when I'm trying to enter the cdkeys. after about 3-6 seconds the screen become "garbled" (random groups of pixels become random colors and the text becomes unreadable.). Once this happens the machine is completely locked up: alt+ctrl+backspace, alt+ctrl+f1, or alt+f4 doesn't. I don't believe it to be a hardware issue since i can boot into windows and play nwn just fine. also I'm not trying to play the game off the window partition. as a matter of fact i don't even have the windows partition to be mounted.

I think I have a misconfiguration somewhere and I know too little to figure it out.
My system:```

Motherboard: Asus a7n8x-e Deluxe
Processor: AMD Athlon XP 3000+
Video: Evga Nvidia Geforce 6800 128MB AGP
hda: IDE Seagate 250GB

```

I installed the 7667 nvidia driver off of apt. After reading around I commented out those two line in the xorg.conf and the dri section but neither offered any improvement. Also why are there so many things in the modules section? do I really need that many. 
/etc/X11/xorg.conf```

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
#	Load	"GLcore"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
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
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800]"
	Driver		"nvidia"
	Option		"NoLogo" "true"
	BusID		"PCI:3:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800]"
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
EndSection

#Section "DRI"
#	Mode	0666
#EndSection

```

uname -a```
Linux Gmm 2.6.12-10-686 #1 Fri Nov 18 12:09:04 UTC 2005 i686 GNU/Linux
```

```

bb002@Gmm:~$ cat /proc/driver/nvidia/cards/0
Model:           GeForce 6800
IRQ:             19
Video BIOS:      05.40.02.12.01
Card Type:       AGP
bb002@Gmm:~$ cat /proc/driver/nvidia/agp/card
Fast Writes:     Supported
SBA:             Supported
AGP Rates:       8x 4x
Registers:       0xff000e1b:0x1f004302
bb002@Gmm:~$ cat /proc/driver/nvidia/agp/status
Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

```
Their was one more thing I was going to include but I forgot what it was now. Besides I think there is plenty of info here already. Does anything look funny? Any ideas on what I should try next?

---

### Post by Perfect Storm on 2005-11-29
Try see if the same happen when using this: [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

---

### Post by bb002 on 2005-11-29
what installers do i want? a platinum version isn't listed and I don't know what differences the platinum version has from the other versions.

---

### Post by Perfect Storm on 2005-11-29
I got platinium Edition too and used the installers above with no problems. The platinium Edition is just NWN with the two expansions.

---

### Post by bb002 on 2005-11-29
Well...While I was waiting on the loki installer to download I put my current nwn install install into a tar.gz file. I then transferred that file to my laptop. Where I left it for the night. Today at work I extractd the tarball and ran nwn (after chown'ing the game, ofcourse). It ran fine after I entered the cdkeys during lunch. I'm running the game on minimal settings so the 8MB onboard intel graphics can attempt to keep up.


My laptop is a Gateway M275 running Ubuntu 5.04 Hoary (tried breezy but it broken everything and i mean EVERYTHING. audio was the only piece of hardware i finally got to work.)

Gateway M275 specs:
1.8 Ghz Centrino
512MB DDR RAM
8MB RAM Intel Graphics (dunno exact make but X uses i810 driver)
40GB Harddrive.
IPW2200BG wireless card.

I'll go ahead and try the loki install but I don't think It'll work since I was able copy my install to another machine and it worked just fine.

---

### Post by bb002 on 2005-12-04
I was about to preform a loki install when I had a sudden idea. I decided to copy the nwncdkey.ini, nwn.ini, and nwnplayer.ini from the install on my laptop to my desktop pc. Now I can play the game! If i rename/delete the nwncdkey.ini I run into the exact problem I had before. So I'm chalking it up to a bug in the cdkey entering dialog. Since I tried my idea I've been playing 8 hours straight...time really flies, could have swore I'd only been playing for 45 minutes.

just for anyone having trouble using the nwn cdkey dialog here's the file format for "nwncdkey.ini"
```

[CDKEY]
Key3=
Key2=
Key1=

```
Key3 is the XP2 cdkey. if you don't have this expansion remove this line.
Key2 is the XP1 cdkey. if you don't have this expansion remove this line.
Key1 is the original cdkey.
Each key is formed by 6 sets of 5 characters separated by a dash and should be in all capitals.
Also the contents of the file are case-sensitive.

---

