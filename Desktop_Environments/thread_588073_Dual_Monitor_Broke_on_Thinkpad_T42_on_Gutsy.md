---
title: "Dual Monitor Broke on Thinkpad T42 on Gutsy"
date: 2007-10-23
forum: Desktop Environments
---

### Post by Ryba on 2007-10-23
I mentioned this  a couple of weeks ago (it just broke during one of the more recent updates during gutsy just prior to stabilization) over here [http://ubuntuforums.org/showthread.php?p=3441431](http://ubuntuforums.org/showthread.php?p=3441431) (closed thread due to gutsy being released and that thread being in development section).

In any case, a perfectly good dual monitor setup no longer works. On top of that, recreating the xorg.conf through the dpkg-reconfigure option doesn't help. And using the "Screens & Graphics" tool to recreate it won't even let me activate the 2nd monitor without disabling the 1st (and if I try to test with 2nd monitor using 1st as disabled the application crashes and dumps a python stacktrace).


This is becoming a serious problem now. I did a quick google search and apparently EVERYONE is having severe issues with ATI and dual monitor out of laptops with ATI cards that are not supported by the fglrx drivers (such as those on the T42)

To give a quick highlight, quick snippets of xorg log file

```
(II) RADEON(0): Max desktop size set to 2304x1024
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf

(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port1: DDCType-2, DACType-1, TMDSType-0, ConnectorType-4
(II) RADEON(0): Port4: DDCType-0, DACType-2, TMDSType-2, ConnectorType-1
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-0 using monitor section Generic Monitor
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI_DDC" initialized.
(II) RADEON(0): DFP table revision: 2
(II) RADEON(0): Output LVDS has no monitor section
(II) RADEON(0): Panel ID string: 1024x768                
(II) RADEON(0): Panel Size from BIOS: 1024x768
(II) RADEON(0): BIOS provided dividers will be used.
(WW) RADEON(0): LVDS Info:
XRes: 1024, YRes: 768, DotClock: 65000
HBlank: 320, HOverPlus: 16, HSyncWidth: 136
VBlank: 38, VOverPlus: 2, VSyncWidth: 6
(II) RADEON(0): Using LVDS Native Mode

(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: DEL  Model: a024  Serial#: 810303827
(II) RADEON(0): Year: 2006  Week: 30
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) RADEON(0): Sync:  Separate
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): Default color space is primary color space
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.312 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): 1280x1024@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Serial No: WH32067Q0LAS
(II) RADEON(0): Monitor name: DELL E197FP
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 31  H max: 80 kHz, PixClock max 140 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0):         00ffffffffffff0010ac24a053414c30
(II) RADEON(0):         1e10010368261e78eeee91a3544c9926
(II) RADEON(0):         0f5054a54b00714f8180010101010101
(II) RADEON(0):         010101010101302a009851002a403070
(II) RADEON(0):         1300782d1100001e000000ff00574833
(II) RADEON(0):         3230363751304c41530a000000fc0044
(II) RADEON(0):         454c4c204531393746500a20000000fd
(II) RADEON(0):         00384b1f500e000a2020202020200058
finished output detect: 0

```Is there any other snippet I need. The external monitor supports 1280x1024 @ 75mhz and the laptop is 1024x768 @ 60mhz. At least that is how it was on drake and fiesty. And even on gutsy up until about a month prior to release.

---

### Post by Ryba on 2007-10-23
FIXED :guitar:

I made the following changes to my xorg.conf

```

Section "Files"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dri"
        Load    "dbe" # Was not here before
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "Radeon Mobility M7"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #VideoRAM       65536
        Option          "ColorTiling"   "false"
        #Option          "MergedFB"      "true"
        #Option          "DynamicClocks"        "on"
        #Option          "CRT2Position"  "RightOf"
        # The next line lets me switch between dual-head and several clone modes of varying resolutions with xrandr.
        #Option         "MetaModes"     "1024x768-1280x1024 1024x768-1024x768 1024x768+1280x1024 1280x1024 1024x768 800x600 640x480"
        #Option          "MergedNonRectangular"  "true"
        # In 1024x768-1280x1024 mode the DPI is correct (100), but in all other modes it is weird.  Try to override
        #Option          "MergedDPI"     "100 100"
        #Option         "CRT2HSync"     "30-81"
        #Option         "CRT2VRefresh"  "56-76"
        #Screen         0
        #Option          "XAANoOffscreenPixmaps" "true"
        Option          "Monitor-LVDS"  "LVDS Monitor"
        Option          "Monitor-VGA-0" "VGA-0 Monitor"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
          Identifier      "VGA-0 Monitor"
          Option          "DPMS"
          Option          "Enable" "0"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon Mobility M7"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Virtual         2304 1024
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```
Then it still starts up with only 1 screen (annoying) but when I run from the command line 

```
xrandr --output VGA-0 --mode 1280x1024 --right-of LVDS
```It activates my 2nd monitor and presto, I have dual screen working again on my T42.

Truely is a shame that the bulletproof xserver and the Screens & Graphics thing still can't help but crashing and burning when trying to do this exact same thing but hopefully they can get that fixed. I'm pretty sure the biggest problem (but don't feel like testing it) is that the Virtual         2304 1024 piece is required cause otherwise the xrandr thinks that the maximum size it is allowed to be is much much smaller then it really should be.

---

### Post by !nkubus on 2007-10-24
Can you post your full xorg.conf, I'm having issues also :(

Thanks a lot

---

### Post by kakao on 2007-10-27
I'd be gratefull for a full xorg.conf, too. I have similar issues on a fresh gutsy system but with intel graphics instead of ATI. Especially "Screens and Graphics" behaves the same. Unfortunatelly I've not had Linux on my laptop until now so I've never had it working.

I also have, on some occations, a cloned destop (with compiz-fusion working) behaving strangely. It seams as if the laptop display works as "borders", e.g. when maximizing windows and new ones are arranged only in that area. But the desktop (background, panel, etc) has the size of the monitor -- background and panel are not shown fully on my laptop display. Strangely though, when I maximize windows that are mainly outsize the boarders of 1024x768 area (laptop display size) they maximize to full 1280x1024 and "zap back" to 1024x768 when I click inside them.

On other occasions (haven't figured out when exactly) Ubuntu starts up on monitor with laptop display showing white with vertical coloured lines or as if I was looking into fog (all grey but different intensities).

I have not much of a clue to what to do.

For others maybe these two links help: [http://blogs.gnome.org/jamesh/2007/09/24/gutsy-upgrade/](http://blogs.gnome.org/jamesh/2007/09/24/gutsy-upgrade/) (problems with Radeon) and [http://www.intellinuxgraphics.org/dualhead.html](http://www.intellinuxgraphics.org/dualhead.html) (more on RandR). Update: And another to a [bug at launchpad]("https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/144641") describing to use XRandR 1.2 for Dual modes in displayconfig-gtk (=Screens and Graphics).

---

### Post by phuonglh on 2007-10-29
I fixed the problem of dual screen on my T42 with Gutsy installed. Simply change my xorg.conf like this:

[INDENT]Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"glx" 
	Load		"vbe"
	Load		"v4l"
EndSection
[/INDENT]
Here, I add the line Load "glx". My screen does not work without this line.

And in the Section device, I removed the Screen 0 and the default Option, add a new Option, like this:

[INDENT]Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	#Screen	0
	#Option		"MergedFB"	"off"
	Option		"DPMS"
[/INDENT]

With these changes, my laptop works perfectly. I can even use Fn-F7 to cycle monitors.

---

### Post by Ryba on 2007-10-31
Sorry for the delays guys. Busy week at work. Yes here is the full xorg config below

```

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
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dri"
        Load    "dbe" # Was not here before
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "imps/2"
        Option          "ZAxisMapping"          "4 5"
        #Option         "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Radeon Mobility M7"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        #VideoRAM       65536
        Option          "ColorTiling"   "false"
        #Option          "MergedFB"      "true"
        #Option          "DynamicClocks"        "on"
        #Option          "CRT2Position"  "RightOf"
        # The next line lets me switch between dual-head and several clone modes of varying resolutions with xrandr.
        #Option         "MetaModes"     "1024x768-1280x1024 1024x768-1024x768 1024x768+1280x1024 1280x1024 1024x768 800x600 640x480"
        #Option          "MergedNonRectangular"  "true"
        # In 1024x768-1280x1024 mode the DPI is correct (100), but in all other modes it is weird.  Try to override
        #Option          "MergedDPI"     "100 100"
        #Option         "CRT2HSync"     "30-81"
        #Option         "CRT2VRefresh"  "56-76"
        #Screen         0
        #Option          "XAANoOffscreenPixmaps" "true"
        Option          "Monitor-LVDS"  "LVDS Monitor"
        Option          "Monitor-VGA-0" "VGA-0 Monitor"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Monitor"
          Identifier      "VGA-0 Monitor"
          Option          "DPMS"
          Option          "Enable" "0"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon Mobility M7"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Virtual         2304 1024
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "AIGLX Layout"
        Screen          "Default Screen" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Option          "AIGLX" "true"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option      "Composite" "true"
EndSection

```
System starts up with the 2nd monitor "blank" (sometimes mirrored) and so just type the following in the command line and it works.

```
xrandr --output VGA-0 --mode 1280x1024 --right-of LVDS
```

---

### Post by kakao on 2007-11-02
> **Ryba said:**
> 
System starts up with the 2nd monitor "blank" (sometimes mirrored) and so just type the following in the command line and it works.


You might want to try and optout the following line for your second monitor:

```
Option          "Enable" "0"
```

As far as I understand it that could help (see [intel's docs]("http://www.intellinuxgraphics.org/dualhead.html") almost at the bottom).

Cheers.
P.S. Mine isn't working yet, unfortunately.

---

