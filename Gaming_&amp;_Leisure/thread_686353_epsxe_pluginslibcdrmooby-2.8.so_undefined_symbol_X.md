---
title: "epsxe: plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetCli"
date: 2008-02-03
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-02-03
epsxe another error:
```
plugins/libcdrmooby-2.8.so: undefined symbol: XftDrawSetCli
```

I tried this [http://www.pbernert.com/html/spu.htm](http://www.pbernert.com/html/spu.htm) but no way.:(:(:(:(

---

### Post by DoktorSeven on 2008-02-03
I didn't need the cdrmooby plugin to use ePSXe at all; I can load ISO and other images into ePSXe fine without it (as well as running CDs).  

I recommend just removing that plugin entirely.

---

### Post by acoustibop on 2008-02-03
It's been some time since I had ePSXe running, but AIR I couldn't get the 2.8 Mooby plugin running either, frenchn00b - I used an earlier version.

I was under the impression that ePSXe needs the Mooby plugin to play images, but DoktorSeven knows the Linux version a great deal better than me, so if he says you don't need it - I guess you don't! ;)

---

### Post by frenchn00b on 2008-02-03
> **DoktorSeven said:**
> I didn't need the cdrmooby plugin to use ePSXe at all; I can load ISO and other images into ePSXe fine without it (as well as running CDs).  

I recommend just removing that plugin entirely.

Whaoo ! it worked ! 
I removed the file with rm : plugins/libcdrmooby-2.8.so
and it goes !!

1000 thanks

I still dont know how to fullscreen this epsxe ...

---

### Post by acoustibop on 2008-02-03
AIR the only way I could get ePSXe to go full screen properly was with Pete's OGL2 plugin.

Any reason why you particularly wanrt to use ePSXE rather than pSX, frenchn00b?  You're going to be running into several problems like this before you get ePSXe running more or less properly - with pSX you can save all the hassle - and get an emulator that works better anyway. ;)

---

### Post by frenchn00b on 2008-02-03
> **acoustibop said:**
> AIR the only way I could get ePSXe to go full screen properly was with Pete's OGL2 plugin.

Any reason why you particularly wanrt to use ePSXE rather than pSX, frenchn00b?  You're going to be running into several problems like this before you get ePSXe running more or less properly - with pSX you can save all the hassle - and get an emulator that works better anyway. ;)

The reason is herewith: [http://doc.freevo.org/GamesConfig](http://doc.freevo.org/GamesConfig)
it is written epsxe, and I just would like something that works as well as Zsnes or dgen, both are working very great. 
xmame-sdl and epsxe is not working easy from the box. I hope it 'll be better in 1year. all games are not working for playstatino and xmame sdl, I know it is the begininng and we should wait a bit longer that the development is finished.
(hence with fullscreen and ESC to exit the game or even lirc with epsxe and xmame would be great to be wokring)
(the machine has no GLX since it is a S3 with a Pentium III )

thanks:guitar:

---

### Post by acoustibop on 2008-02-03
As far as I can see, frenchn00b, Freevo seems to work essentially by booting the emulator from a script, which means pSX will work as well with it as ePSXe, plus pSX will work a lot better.  In fact, I used to start some of the pre-release pSX Linux WIPs from scripts, before Ultima wrote a version of his pSX frontend for Linux.

In fact, some features are going to be difficult to implement like this in ePSXe (quite apart from getting full screen to work - which you may not be able to) - switching between digital and analog modes will be one.  Many older Playstation games don't support analog controllers, which means the controller has to be configured as a digital one.  You can do this in pSX with a switch; in ePSXe, you not only need to set the -analog switch to use an analog controller, you also have to change the settings in the plugin configuration - which may not be possible from a script.

Here's a list of the pSX Linux version switches:```
psx [options] <path to cd> [<ppf file>] [<save state>]
Options: -w                 Windowed
         -f                 Full screen
         -c{i/r}            R3000 CPU mode (interpreter/recompiler)
         -C{i/r}            R5900 CPU mode
         -r                 Enable event rescheduling
         -s                 Disable frame skipping
         -2                 PS2 mode
         -t                 Start with status display enabled
         -F                 Disable pause
         -a<slot>,<fname>   Insert memory card
         -p-                No pad in port 0
         -A                 Disable async cd access (always block)
         -P                 Disable 50hz (always use 60hz)
         -p<mode>           Pad mode
                            0 - SCPH-1010: Normal pad
                            1 - SCPH-1150: Analog+rumble
                            2 - SCPH-1200: Dualshock
```
As you can see, there are very options you'd need for running games that aren't there - about the only one missing you might want on a per game basis is changing the BIOS, and AFAIK you can't do that in ePSXe, either.  There is an excellent pSX frontend, [Ultima's pSX Frontend]("http://psxemulator.proboards54.com/index.cgi?board=news&action=display&thread=1156715263"), which can do this by writing to pSX' configuration file, though.

---

### Post by frenchn00b on 2008-02-03
pSX dwload: 
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)
  
well ... I got a problem houston
```
   pSX$ ./pSX 

(pSX:7299): GdkGLExt-WARNING **: Window system doesn't support OpenGL.
```

here is my xorg.conf:
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/X11R6/lib/X11/fonts/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
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
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
Option "Composite" "Enable"
EndSection



and my video card is : 
-pci
          description: Host bridge
          product: 82815 815 Chipset Host Bridge and Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
        *-display
             description: VGA compatible controller
             product: 82815 CGC [Chipset Graphics Controller]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 02
             size: 64MB
             width: 32 bits
             clock: 66MHz
             capabilities: vga bus_master cap_list
             configuration: latency=0
             resources: iomemory:44000000-47ffffff iomemory:40300000-4037ffff irq:10
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@00:1e.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
           *-network
                description: Ethernet interface
                product: 82801BA/BAM/CA/CAM Ethernet Controller
                vendor: Intel Corporation
                physical id: 8
                bus info: pci@02:08.0
                logical name: eth0
                version: 01

---

### Post by acoustibop on 2008-02-03
What are the first several lines that you get for glxinfo, frenchn00b?

I don't really know much about the Intel integrated video chips, but I'm sure other people run pSX successfully with them.  Have you tried installing a proprietary driver for it (open the Restricted Drivers Manager and see if there's a driver offered for it - if there is, install it)?

What sort of machine are you running this on?

---

