---
title: "Getting a Higher Resolution."
date: 2005-07-19
forum: Desktop Environments
---

### Post by capi on 2005-07-19
I'm in a default install of Ubuntu, the highest resolution it will give me is 1024x768@85, however I want 1152x864@75. I know it's possible, as I used it on windoze. [Monitor Specs](http://www.emachines.com/support/product_support.html?cat=monitor&subcat=CRT&model=eView+17f2) 

Relative Section in /etc/X11/xorg.conf ...

EDITED TO INCLUDE NEWER CONFIG...
```

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	65536
EndSection

Section "Monitor"
	Identifier	"eView 17f2"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"eView 17f2"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864" "1024x768"
	EndSubSection
EndSection

```

I've been told to use a few different modlines, the one above was gotten off of the command

[$ gtf 1152 864 70](http://www.ubuntuforums.org/showthread.php?p=227440#post227440) 

I was trying `75' before, but I thought it may be two high a refresh rate(though 75 is what i get in Windoze). I'm not sure why it's not showing it, the Gnome resolution tool is sticking everything at @85, is there a way I can tell grub I want @75 instead?, maybe then it would allow a different screen size? Please help. :D

~ capiCrimm

---

### Post by az on 2005-07-19
Go into the console

CTRL-ALT-F1
log in
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
in monitor config, pick medium and find the right resolution and frequency.
sudo /etc/init.d/gdm start

You need to kill X for it to autodetect your hardware properly 100 percent of the time.

---

### Post by Teroedni on 2005-07-19
We just have to add another resolution and it should work in 1152x864

You can try the xorg.conf i altered , but i cant promise it works as intel chipset is not the easiest to work with




Section "Monitor"
	Identifier	"emachines"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160  
	# 1152x864 @ 70.00 Hz (GTF) hsync: 63.00 kHz; pclk: 96.77 MHz
	Modeline "1152x864_70.00"  96.77  1152 1224 1344 1536  864 865 868 900  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"emachines"
	DefaultDepth	24	
        SubSection "Display"
                Depth           8
                Modes           "1280x1024"  "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes            "1280x1024"  "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024"   "1152x864" "1024x768"
	EndSubSection
	SubSection "Display"
                Depth           24
                Modes            "1280x1024"  "1152x864" "1024x768"
        EndSubSection
EndSection


I see Azz have posted, so your probably better of listening to him;)

---

### Post by capi on 2005-07-19
Nope, I've tried dpkg-reconfigure xserver-xorg twice now. The only difference it makes is setting the res lower initially(@70 I  think instead of @85), I just did it again to be sure and same results... :\ .

Is there something I can do to override the resolution for Gnome?

---

### Post by Jet2k5 on 2005-07-19
I just had to do the same for my new monitor.  Post the WHOLE section labeled " Screen ".  You posted some of it, but I know there has to be more.

---

### Post by capi on 2005-07-19
@Jet2k5

That is all of it currently. Normally it repeats for different bits, but to make it simplier for now I deleted those.

What I had before was...

```

        SubSection "Display"
                Depth           8
                Modes            "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes            "1152x864" "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes            "1152x864" "1024x768"
   EndSubSection
   SubSection "Display"
                Depth           24
                Modes            "1152x864" "1024x768"
        EndSubSection 

```

I can throw that back in the config file if you think it will do somehting. I don't have 1 and 4 above, since my monitor doesn't get those, but if you want me to throw the above back in I may as well include 1 and 4 as well. 

Jet2k5 what did you do to get the screen working correctly? Do you mean spkg-reconfigure like azz said???

---

### Post by DancingSun on 2005-07-19
In the monitor section, try commenting out both of the refresh rates.  That's what I did, and it seems to auto detect the supported refresh rates now.

Edit: This assumes that you have a relatively modern monitor.

---

### Post by capi on 2005-07-19
[QUOTE=DancingSun]In the monitor section, try commenting out both of the refresh rates.  That's what I did, and it seems to auto detect the supported refresh rates now.

Edit: This assumes that you have a relatively modern monitor.[/QUOTE]
 No, DancingSun that only gets me 640x480@60... :\

---

### Post by az on 2005-07-19
I dunno.

Maybe the linux driver for your graphics card works differently than the windows driver?  Maybe you are using a lower color depth in windows (16 bit?)

You know, many of the drivers for linux are reverse engineered, so you cannot expect the same results when the manufacturer does not even help.

---

### Post by DancingSun on 2005-07-19
How come you only have 2 resolution modes?  Did you edit it yourself?  What's the default?

I have a Samsung 950p (something like that) monitor paired with a nVidia Geforce 6600GT.  The only thing I did was install the nVidia drivers from Synaptic and then editing the "monitor" section of the xorg.conf.  I tried to set the resolution and refresh rate by editing the refresh rates and the modeline before, but it didn't give me optimal refresh rate at the resolution I want (the highest it would go was 85hz on resolutions of 1024x768 and lower).  But after I commented out the refresh rates, I was able to get 100hz at 1024x768.

---

### Post by banasw01 on 2005-08-26
I have NVIDIA Geforce FX 5900XT and I am running at 1152x864 24 color.  Below is my xorg.conf.  I an a newbie, but I got 1152x864 to work so I'm happy :)  I had to increase  VertRefresh 50-80 because it was at 50-70 originally.

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

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
	Identifier	"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	50-80
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV35 [GeForce FX 5900XT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1152x864"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1152x864"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1152x864"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1152x864"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1152x864"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1152x864"
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

### Post by varunus on 2005-08-26
capi,

I see you have an Intel i810 card.  Have you tried 855resolution?
Here's a howto:
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)

---

