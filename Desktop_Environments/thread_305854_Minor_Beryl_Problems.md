---
title: "Minor Beryl Problems"
date: 2006-11-24
forum: Desktop Environments
---

### Post by Cbeck527 on 2006-11-24
Hi!
I have been reading posts on this forum for a while now and this is the first time I am posting.
I recently installed beryl on my IBM T30 laptop. I configured the radeon driver, got beryl installed and working, and I tweaked the settings to my liking. However, I have two problems. Whenever I maximize and app to fullscreen, the title bar and _ - X all disappear and it is just a white bar. The weird thing is I can still click the buttons. Also, when I launch Java applications, specifically Limewire and Frostwire, the border appears but the inside is completely blank. I found that changing the window manager back to MetaCity fixes that problem, but quite frankly, I hate that theme. I would really like to know how to fix this.

I have included screenshots to hopefully help:

This is it working:
[IMG]http://img300.imageshack.us/img300/7563/berylworkinghg0.png[/IMG]

This is it not working:
[IMG]http://img300.imageshack.us/img300/6232/berylnotworkingbv9.png[/IMG]

Thanks in advance,
Cbeck

---

### Post by Cbeck527 on 2006-11-24
bump

---

### Post by Random20230808 on 2006-11-25
Give some more details about your installation.
Have you installed the flgrx drivers for your ATI card?
Have you installed Xgl or Aiglx?
Edgy or Dapper?
Post your xorg.conf (/etc/X11/xorg.conf)

---

### Post by AgenT on 2006-11-26
I have the same problem.

ATI Technologies Inc Radeon Mobility M6 LY
AIXGL
Edgy
beryl 0.1.1
Here is my truncated xorg.conf:
```
Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mo
bility 9000]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option          "DynamicClocks"         "on"
#       Option          "RenderAccel"           "off"
        #Beryl Options
        Option          "TripleBuffer"          "true"
        Option          "AGPMode"               "8"
        Option          "AccelMethod"           "EXA"
        Option          "ColorTiling"           "on"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mo
bility 9000]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        # Beryl
        Option          "AddARGBGLXVisuals"     "True"
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection

Section "DRI"
        Mode    0666
EndSection
```Everything under the "Beryl" headings in each section are Beryl specific optimizations that I have tried. The maximize window problem happens with and without these optimizations.

---

### Post by Cbeck527 on 2006-11-26
> **emsyr said:**
> Give some more details about your installation.
Have you installed the flgrx drivers for your ATI card?
Have you installed Xgl or Aiglx?
Edgy or Dapper?
Post your xorg.conf (/etc/X11/xorg.conf)
I'm running Ubuntu 6.10 (Edgy Eft). After following many guides, I finally got Beryl running after I put "radeon" in the driver field of the xorg.conf. For some reason (maybe it was not installed properly) when putting flgrx in the driver feild, Xserver failed to start and I had to login and edit the xorg.conf through the console. Honestly, I have no idea if Xgl or Aiglx is installed, is there a way to find that out?
Here is my xorg.conf file:
```
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"ATI RADEON 7500 MOBILE"
	Driver		"radeon"
Driver		"radeon"
	Option		"AGPFastWrite" "yes"
	Option		"AGPMode" "4"
	Option		"ColorTiling" "on"
	Option		"EnablePageFlip" "true"
	Option		"AccelMethod" "EXA"
	Option		"RenderAccel" "true"
	Option		"DRI" "true
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
        Option "AddARGBGLXVisuals" "True"
	Identifier	"Default Screen"
	Device		"ATI RADEON 7500 MOBILE"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by andril on 2006-11-26
I would like to start from scratch I just reinstalled Ubuntu 6.10 Edgy - I need to get Beryl running
I am using the following

nVIDIA 5200 256mb AGP  :-D 
AMD Athlon 2.0 ghz
1gb of DDRAM

Thanks In Advance

---

### Post by AgenT on 2006-11-26
> **andril said:**
> I would like to start from scratch I just reinstalled Ubuntu 6.10 Edgy - I need to get Beryl running
I am using the following

nVIDIA 5200 256mb AGP  :-D 
AMD Athlon 2.0 ghz
1gb of DDRAM

Thanks In Advance
This thread is about Beryl problems, not a how-to on installing Beryl. Read [this thread]("http://ubuntuforums.org/showthread.php?t=272104") for more information. In the future, please do not hijack threads.

---

### Post by Random20230808 on 2006-11-27
You have to install and run Xgl or Aiglx before you run Beryl.
Otherwise you cannot run Beryl.
Try [https://help.ubuntu.com/community/CompositeManager]("https://help.ubuntu.com/community/CompositeManager") to install one.
Personally I have managed Xgl to work in my computer (Aiglx didn't work).

---

### Post by tribaal on 2006-11-27
If you didn't install XGL yourself then you're using AIGLX (since it comes default with Edgy).

If you use the binary ATI drivers (the ones you get from ati.com), you'll need to install XGL as their driver doesn't work well with AIGLX (for 3d).
If the open source "radeon" drivers are good enough for you (like they are for me), you'll get Beryl to work with AIGLX without problems. It's just a tad slower than with XGL.

If you have an nVidia card - rejoice: you can use the latest baddest nVidia drivers (from nvidia.com) with the default AIGLX. The performance is great, and nVidia provides a nice graphical config utility :)

Hope this helps

- trib'

---

### Post by AgenT on 2006-11-27
> **emsyr said:**
> You have to install and run Xgl or Aiglx before you run Beryl.
Otherwise you cannot run Beryl.
Try [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager) to install one.
Personally I have managed Xgl to work in my computer (Aiglx didn't work).
Not true. AIGLX is by far the easiest method of getting Beryl to work. There is absolutely NO configuration or additional packages needed. Just apt-get install beryl and you are done. Of course, you have to have AIGLX enabled and your card needs to be supported.

And AIGLX gives great performance. It even works with default settings on a video card with 16mb ram!!

---

### Post by deep.tinker77 on 2006-11-27
> **Cbeck527 said:**
> Hi!
I have been reading posts on this forum for a while now and this is the first time I am posting.
I recently installed beryl on my IBM T30 laptop. I configured the radeon driver, got beryl installed and working, and I tweaked the settings to my liking. However, I have two problems. Whenever I maximize and app to fullscreen, the title bar and _ - X all disappear and it is just a white bar. The weird thing is I can still click the buttons. Also, when I launch Java applications, specifically Limewire and Frostwire, the border appears but the inside is completely blank. I found that changing the window manager back to MetaCity fixes that problem, but quite frankly, I hate that theme. I would really like to know how to fix this.


Thanks in advance,
Cbeck

I have the same exact problem, only I'm running an intel i810 graphics card. I don't mean to hijack the thread, but since both of us are having the same problem, I thought I'd just post here. Here is my X11.conf:

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
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Grap
hics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Grap
hics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Thanks for any help

---

### Post by Cbeck527 on 2006-12-07
FIXED!!!! 

Add:

Option          "AGPSize" "32"

to your xorg.conf under the graphics section!!!

---

### Post by adds2one on 2007-01-11
> **Cbeck527 said:**
> FIXED!!!! 

Add:

Option          "AGPSize" "32"

to your xorg.conf under the graphics section!!!

I did this but still have the same problem of blank window borders when maximized. :(

---

### Post by jasutton on 2007-02-01
> **Cbeck527 said:**
> FIXED!!!! 

Add:

Option          "AGPSize" "32"

to your xorg.conf under the graphics section!!!

I've got a Thinkpad T40 (Radeon Mobility 7500), and this worked for me.  Thanks :)

---

### Post by nelio2k on 2007-03-21
The AGPSize fix works for me too! I've been trying forever to get it to work. Thanks!
By the way, I have an IBM Thinkpad R32 with a really old 16MB ATI Mobility M6. 

I set the AGPMode to 1, and the size to 32. If I set the AGPMode to something bigger it would distort my screen. Hope this helps anyone. 

Now the only problem I have with Beryl is its slow scroll. I don't know if anyone has come up with a solution for that yet, tho...

Just in case if you need my xorg.conf to refer, here it is:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility M6 LY [Radeon Mobility 9000]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
	Option 		"DRI" 	"true"
	Option 		"ColorTiling" "on"
	Option 		"EnablePageFlip" "true"
	## Some may experience very poor performance without hashing the following line.
	#Option 	"AccelMethod" "EXA"
	Option		"AccelMethod" "XAA"
	## If above is hashed, change the following to "XAANoOffscreenPixmaps"
	Option		"XAANoOffscreenPixmaps"	"on"
	Option 		"EXANoOffscreenPixmaps"
	Option 		"RenderAccel" "true"
	#Option 	"AGPMode" "4" <- x may be 1, 2, 4, or 8 depending on your system
	Option		"AGPMode" "1"
	Option		"AGPSize" "32"
	Option 		"AGPFastWrite" "on"
	Option		"RenderAccel"	"true"

---

