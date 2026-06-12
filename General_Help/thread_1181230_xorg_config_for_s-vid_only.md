---
title: "xorg config for s-vid only"
date: 2009-06-07
forum: General Help
---

### Post by Malefic on 2009-06-07
I have an intel BOXD945GCLF2 board running 9.04, that I'm trying to hook up to an old CRT TV over S-VID. The display looks fine until it gets into gdm, where it gets ripped/distorted.

Setting the old TV to 640x480 just makes it a much smaller distorted image.

Any help would be appreciated.

lspci:
```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:00.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)

```

xorg.conf.new:
```

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
	Load  "glx"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

```

xrandr:
```

Screen 0: minimum 320 x 200, current 1280 x 960, maximum 1600 x 1600
VGA disconnected (normal left inverted right x axis y axis)
TV-1 connected 1280x960+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1600x1024      60.2  
   1280x1024      60.0  
   1280x1024@60.00   60.0  
   1440x900       59.9  
   1280x960       60.0* 
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   1024x768@60.00   60.0  
   920x766@60.00   60.0  
   832x624@60.00   60.0  
   800x600        60.3  
   800x600@60.00   60.0  
   720x576@60.00   60.0  
   704x576@60.00   60.0  
   720x540@60.00   60.0  
   720x480@60.00   60.0  
   640x480        59.9

```

---

### Post by argail1980 on 2009-06-07
Have you tried with a computer monitor to make sure there's not something else wrong?

anyway:
in your xorg.conf is still the standard monitor section, as if the TV wasn't recognized properly. Try to get some more information into that section.. usually it looks something like:

```
# Section „Monitor“
# Identifier "Monitor[1]" #TV
# HorizSync 30-50
# VertRefresh 50 #or 60
# EndSection

```

then you need a section the s-video output

```
# Section „Device“
# Driver „nvidia“
# Identifier „Device[1]“
# Screen 1
# Option "TVOutFormat" "Composite" #or SVIDEO (or RGB)
# Option "TVStandard" "PAL-G" # at least in Germany
# Option "ConnectedMonitor" "Monitor[1]"
# BusID "PCI:1:0:0"
# EndSection

```

I got those from [here]("http://wiki.ubuntu-forum.de/index.php/TV-Out_einrichten_(Nvidia)#Einrichten__des_TV-Out_mittels_der_xorg.conf").. watch out, some details could be specific for Germany, like the PAL-G standard. 

Google for how to set up a TVout via xorg.conf, there should be something that matches your system

---

### Post by Malefic on 2009-06-07
I'm not sure how to see the real xorg.conf since they obfuscated everything.
The previous one I posted was what an X -configure gave me.


edit: i have no other devices to test the s-vid output.. but it looks fine before it hits gdm. Also for clarification I'm in NTSC corner of the world.


edit2: this xorg.conf gives the same tearing

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "dri"
	Load  "dri2"
	Load  "dbe"
	Load  "record"
	Load  "glx"
	Load  "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	HorizSync 30-50
	VertRefresh 50
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	Option "TVOutFormat" "SVIDEO"
	Option "TVStandard" "NTSC"

	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth	24
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes "640x480_50"
	EndSubSection
EndSection

```

---

### Post by Malefic on 2009-06-07
ive tried the following modes for 24 and 16 bit depth with no success:

640x480_60
640x480_50
640x480_30
640x480_24
720x480_60
720x480_50
720x480_30
720x480_24

---

### Post by kalesh7 on 2009-06-07
try something like this for your device section
> 
Section "Device"
[INDENT]        Identifier  "Card0"
        Driver      "intel"
        VendorName  "Intel Corporation"
        BoardName   "82945G/GZ Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
        Option      "TVOutFormat" "SVIDEO" 
        Option      "TVStandard" "PAL-B"
        Option      "ConnectedMonitor" "TV"[/INDENT]
EndSection


---

### Post by Malefic on 2009-06-07
The only difference seemed to be: Option "ConnectedMonitor" "TV"

Same distorted output.

```

sudo X -config /home/jkrentz/xorg.conf.new

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux htpc 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun  7 19:04:34 2009
(++) Using config file: "/home/jkrentz/xorg.conf.new"
(EE) intel(0): First SDVOB output reported failure to sync
get fences failed: -1
param: 6, val: 0
output modeline:
input modeline:
get fences failed: -1
param: 6, val: 0

```

---

### Post by sandy8925 on 2009-06-08
You said your TV was NTSC. So you should probably use:

Option "TVStandard" "NTSC"

instead of

Option "TVStandard" "PAL-B"

as kalesh7 said

---

### Post by sandy8925 on 2009-06-08
I had a simlilar problem where I connected my Nvidia graphics card to the TV through Svideo using some cable that came along with the graphics card. 

One side of this cable connects to the Svideo port on the graphics card and the other side has 4 outputs: one is a normal video cable connection (like what you use for connecting DVD player to TV) and the other 3 are compnonent connections.

I connected using both the normal and the component connections. The output through the normal cable was fine. The output through the component cable was much more clearer but the colours weren't proper; they were sort of purplish. But now after using the newer nvidia drivers it works fine.

---

### Post by Malefic on 2009-06-08
> You said your TV was NTSC. So you should probably use:

Option "TVStandard" "NTSC"

I've had it set to NTSC.

I guess I could test an S-VID to composite connection, but I don't have an adapter.

I think the problem is the HorizSync and VertRefresh attributes. These aren't getting picked up automatically and I have no idea what to set them to.

---

### Post by Malefic on 2009-06-09
bump

---

