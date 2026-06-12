---
title: "List your unresolved problems with XGL"
date: 2006-09-20
forum: Desktop Environments
---

### Post by rianquinn on 2006-09-20
I have run into several people talking about problems with XGL. Some are graphics problems, others are driver problems. In this forum:

[COLOR="Red"][SIZE="4"]List What Doesn't Work For You using XGL[/SIZE][/COLOR]

[COLOR="Red"]NOTE: 
    1) Please be specific to allow plenty of detail for debugging
    2) DO NOT POST anything but problems. Otherwise the list will be hard to read.[/COLOR]

Hopefully, this thread will help the developers of XGL by giving them a list fo bugs and things to look at.

My Top two:

    1) Wacom Support. The XInput Driver doesn't load when XGL is turned on.

Details:
    Without XGL, I can use by TabletPC with GIMP and Xournal with pressure sensitivity. Both applications show the XInput being enabled. When I use XGL both Applications no long allow the use XInput of XInput. The result is the eraser don't work, and the applications draw choopy lines instead of smooth consistant lines.
 
    2) Numpad problem. My numpad doesn't work correctly. 

Details:
    When XGL is NOT enabled, my numpad works perfectly fine. When XGL is enabled, my numpad simply ignores the NUM-LOCK key. Doesn't matter what I set it to (On/Off). The numpad always acts as if the NUM-LOCK key is "OFF". 

Good Luck and Happy Posting :p

---

### Post by g1tlh on 2006-09-20
Just installed it and the only immediate problem I am seeing is bad redrawing  on scrolling in GTK2 treelists and such like (eg the list of folders in evolution)

Running the mouse up and down the window or pressing the "display desktop" icon twice to redraw the screen seems to clear it.

I am up to date (as of 10 mins ago) on Edgy, using nvidia on an FX5700 with two 1280x1024 monitors in TwinView.

---

### Post by ilovenicotine on 2006-11-13
> **rianquinn said:**
> 
    2) Numpad problem. My numpad doesn't work correctly. 

Details:
    When XGL is NOT enabled, my numpad works perfectly fine. When XGL is enabled, my numpad simply ignores the NUM-LOCK key. Doesn't matter what I set it to (On/Off). The numpad always acts as if the NUM-LOCK key is "OFF".

I have the same problem.  It also disables a few other buttons such as Ctrl-Alt + Left/Right and Super.  I have found a simple way around it, but it is still very annoying.  

I go to Main Menu>System>Preferences>Keyboard>Layout>Keyboard Model>"..."

then select any keyboard, hit "OK", hit "..." again and choose my keyboard (Generic 104-key PC) hit "OK">close and everything is fine.

with XGL/Beryl off from startup it doesn't happen.

---

### Post by SlySmiles on 2006-11-14
Not sure if this is totally relevant as I'm 100% sure exactly whats happening...
It looks like you can't have multiple users with XGL (i.e. user switching is no longer possible).

This makes XGL / Beryl impossible for me (2 users on 1 machine).

If this isn't the case please let me know, as XGL / Beryl combination is fantastic!

---

### Post by rabid emu on 2006-11-14
Going to a console (ctrl+alt+f1-f6) doesn't work at all.  Just gives me a fuzzy colored screen.  Other than that it works pretty well.

---

### Post by Slim on 2006-11-14
Attempting to start beryl gives:

```
sauce:jg:~> beryl-manager 
sauce:jg:~> Error: couldn't find RGB GLX visual
Segmentation fault
compiz.real: Another window manager is already running on screen: 0
compiz.real: Another window manager is already running on screen: 1
compiz.real: No manageable screens found on display :0.1
```

.. then the WM won't start on attempting to restart KDE subsequently. So, a bit of a dead loss so far.

GeForce4 MX 4000, nvidia beta driver compiled locally, Kubuntu 6.10, kernel 2.6.17-10-386. Dual head setup.

---

### Post by eldorel on 2006-11-17
The lack of any xinerama/dual head support. I have 3 different computers that I use with either xinerama or seperate displays. My laptop uses twinview, but the other two both use multiple video cards instead of one dual head card. On one I use three separate displays, which i can't do with just one card, and the other is using two seperate cards because i don't feel the need to replace perfectly working hardware just for one, somewhat useful, program.

I am able to use Xgl, AIGLX, Beryl, and Compiz all perfectly well when i limit my setup to just one card, but start running into major problems when attempting to use dual or triple heads. 

Xgl is a great technology, and I would love to be able to use it, but as long as it causes me to lose functionality that i've had for 10+ years, it's just a toy.

---

### Post by hokutonoken on 2006-11-17
I can't load XGL on my Acer Aspire laptop, no matter what I try.

I asked for advice but no one has given me any solution until now.

Upon reboot, I get a black screen followed by the following X server error message:

NVIDIA(0): Failure reading maximum pixel clock value for display device
NVIDIA(0): TV-0

I have a Nvidia fx Go5200 and both drivers and XGL modules are correctly installed

xorg.conf and gdm.conf-custom are set according to Ubuntu XGL howto.

I guess it depends on "Monitor" or "screen" section of my xorg.conf

Here they are:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Option "NoLogo" "1"
Option "NvAGP" "1"
HorizSync 28-51
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV34M [GeForce FX Go5200]"
Monitor "Generic Monitor"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection


What do you think? 
I'm desperate, tried everything with no luck..

---

### Post by hokutonoken on 2006-11-18
I considered there are two other X server warnings (after the error already reported) which may be causing XGL to crash.

The first is:

The XKEYBOARD keymap compiler (xkbcomp) reports:
 > Warning:            Type "ONE_LEVEL" has one level, but <RALT> has 2 simbols
 >                              Ignoring extra simbols

and the next (and last) is:

FreeFontPath: FPE "usr/share/fonts/misc" refcount is 2, should be 1; fixing.

I think they have something to do with fonts folder loading.


I already tried googling and found many other people have the same problem, which isn't fatal to Gnome and KDE, but apparently keeps XGL from running.

Unfortunately I haven't found any solution.And there seem to be none out there.

Here is an example.
[http://forums.kororaa.org/viewtopic.php?t=700&postdays=0&postorder=asc&start=0](http://forums.kororaa.org/viewtopic.php?t=700&postdays=0&postorder=asc&start=0)

Many people complain Koroora doesn't start.
The symptoms are the same: three flashes on the screen an then Blue Scrren Of Death-

I also set a longer gdm load time (in gdm.conf), but it continues crashing.

What do you think?

---

### Post by hokutonoken on 2006-11-18
Here are my configuration files and X error log, I'd be glad if someone would be so kind to give them a look.

>>>xorg.conf

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
	FontPath	"/usr/share/X11/fonts/misc"
#	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Option "NoLogo" "1"
	Option "NvAGP" "1"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
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
#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
EndSection

#Section "DRI"
#	Mode	0666
#EndSection


>>>here is gdm.conf-custom


# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
# 
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
# 
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
# 
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
# 
# NOTE: Lines that begin with "#" are considered comments.
# 
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]# Override display 1 to use Xgl
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true


>>and finally, here is xorg error log


X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.15.7 i686
Current Operating System: Linux Mozilla 2.6.15-27-k7 #1 SMP PREEMPT Sat Sep 16 02:35:20 UTC 2006 i686
Build Date: 16 March 2006
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.93.log", Time: Sat Nov 18 11:49:20 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "NVIDIA Corporation NV34M [GeForce FX Go5200]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.8
	X.Org XInput driver : 0.5
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,0204 card 1025,006e rev 00 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 1106,1204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:2: chip 1106,2204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:3: chip 1106,3204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:4: chip 1106,4204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:00:7: chip 1106,7204 card 0000,0000 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b188 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0a:0: chip 17fe,2220 card 1468,0305 rev 00 class 02,00,00 hdr 00
(II) PCI: 00:0b:0: chip 104c,ac8e card 2000,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 00:0b:1: chip 104c,ac8e card 2800,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 00:0b:2: chip 104c,802e card 1025,006e rev 00 class 0c,00,10 hdr 80
(II) PCI: 00:10:0: chip 1106,3038 card 1025,006e rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1025,006e rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1025,006e rev 80 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3104 card 1025,006e rev 82 class 0c,03,20 hdr 00
(II) PCI: 00:11:0: chip 1106,3177 card 1106,3177 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:1: chip 1106,0571 card 1025,006e rev 06 class 01,01,8a hdr 00
(II) PCI: 00:11:5: chip 1106,3059 card 1025,0046 rev 50 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 1025,0046 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1025,006e rev 74 class 02,00,00 hdr 00
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0324 card 1025,006e rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:11:0), (0,2,5), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x32000000 - 0x33ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x31ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (0:11:1), (0,6,9), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[1] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x36000000 - 0x37ffffff (0x2000000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x34000000 - 0x35ffffff (0x2000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34M [GeForce FX Go5200] rev 161, Mem @ 0xc1000000/24, 0xe0000000/27
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xd0000000 from 0xdfffffff to 0xcfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xc0006800 - 0xc00068ff (0x100) MX[B]
	[1] -1	0	0xc0006400 - 0xc00064ff (0x100) MX[B]
	[2] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[3] -1	0	0xc0005800 - 0xc0005fff (0x800) MX[B]
	[4] -1	0	0xc0005000 - 0xc00057ff (0x800) MX[B]
	[5] -1	0	0xc0006000 - 0xc000601f (0x20) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[12] -1	0	0x00001c80 - 0x00001c8f (0x10) IX[B]
	[13] -1	0	0x00001c60 - 0x00001c7f (0x20) IX[B]
	[14] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[15] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xc0006800 - 0xc00068ff (0x100) MX[B]
	[1] -1	0	0xc0006400 - 0xc00064ff (0x100) MX[B]
	[2] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[3] -1	0	0xc0005800 - 0xc0005fff (0x800) MX[B]
	[4] -1	0	0xc0005000 - 0xc00057ff (0x800) MX[B]
	[5] -1	0	0xc0006000 - 0xc000601f (0x20) MX[B]
	[6] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[7] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[8] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[10] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[11] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[12] -1	0	0x00001c80 - 0x00001c8f (0x10) IX[B]
	[13] -1	0	0x00001c60 - 0x00001c7f (0x20) IX[B]
	[14] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[15] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[16] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0006800 - 0xc00068ff (0x100) MX[B]
	[5] -1	0	0xc0006400 - 0xc00064ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0005800 - 0xc0005fff (0x800) MX[B]
	[8] -1	0	0xc0005000 - 0xc00057ff (0x800) MX[B]
	[9] -1	0	0xc0006000 - 0xc000601f (0x20) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[16] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x00001c80 - 0x00001c8f (0x10) IX[B]
	[19] -1	0	0x00001c60 - 0x00001c7f (0x20) IX[B]
	[20] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[21] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.0.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.5
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.0.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.8
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0006800 - 0xc00068ff (0x100) MX[B]
	[5] -1	0	0xc0006400 - 0xc00064ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0005800 - 0xc0005fff (0x800) MX[B]
	[8] -1	0	0xc0005000 - 0xc00057ff (0x800) MX[B]
	[9] -1	0	0xc0006000 - 0xc000601f (0x20) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[16] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[17] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[18] -1	0	0x00001c80 - 0x00001c8f (0x10) IX[B]
	[19] -1	0	0x00001c60 - 0x00001c7f (0x20) IX[B]
	[20] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[21] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[22] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xc0006800 - 0xc00068ff (0x100) MX[B]
	[5] -1	0	0xc0006400 - 0xc00064ff (0x100) MX[B]
	[6] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[7] -1	0	0xc0005800 - 0xc0005fff (0x800) MX[B]
	[8] -1	0	0xc0005000 - 0xc00057ff (0x800) MX[B]
	[9] -1	0	0xc0006000 - 0xc000601f (0x20) MX[B]
	[10] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[11] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[19] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[20] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[21] -1	0	0x00001c80 - 0x00001c8f (0x10) IX[B]
	[22] -1	0	0x00001c60 - 0x00001c7f (0x20) IX[B]
	[23] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[24] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[25] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[26] 0	0	0xe80003b0 - 0xe80003bb (0xc) IS[B]
	[27] 0	0	0xe80003c0 - 0xe80003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "1"
(**) NVIDIA(0): Option "NvAGP" "1"
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "true"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Use of NVIDIA internal AGP requested
(EE) NVIDIA(0): Failure reading maximum pixel clock value for display device
(EE) NVIDIA(0):     TV-0.
(II) NVIDIA(0): NVIDIA GPU GeForce FX Go5200 at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.05
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX Go5200 at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) NVIDIA(0):     NVIDIA Default Flat Panel (DFP-0)
(--) NVIDIA(0): NVIDIA TV Encoder (TV-0): 100.0 MHz maximum pixel clock
(--) NVIDIA(0): TV encoder: NVIDIA
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[1] 0	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xc0006800 - 0xc00068ff (0x100) MX[B]
	[7] -1	0	0xc0006400 - 0xc00064ff (0x100) MX[B]
	[8] -1	0	0xc0000000 - 0xc0003fff (0x4000) MX[B]
	[9] -1	0	0xc0005800 - 0xc0005fff (0x800) MX[B]
	[10] -1	0	0xc0005000 - 0xc00057ff (0x800) MX[B]
	[11] -1	0	0xc0006000 - 0xc000601f (0x20) MX[B]
	[12] -1	0	0xd0000000 - 0xcfffffff (0x0) MX[B]O
	[13] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xc1000000 - 0xc1ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[21] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[22] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[23] -1	0	0x00001c80 - 0x00001c8f (0x10) IX[B]
	[24] -1	0	0x00001c60 - 0x00001c7f (0x20) IX[B]
	[25] -1	0	0x00001c40 - 0x00001c5f (0x20) IX[B]
	[26] -1	0	0x00001c20 - 0x00001c3f (0x20) IX[B]
	[27] -1	0	0x00001c00 - 0x00001c1f (0x20) IX[B]
	[28] 0	0	0xe80003b0 - 0xe80003bb (0xc) IS[B]
	[29] 0	0	0xe80003c0 - 0xe80003df (0x20) IS[B]
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "it"
(**) Generic Keyboard: XkbLayout: "it"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
FreeFontPath: FPE "/usr/share/X11/fonts/misc" refcount is 2, should be 1; fixing.



>>That's it. Thanks in advance.

---

### Post by rei682 on 2006-11-18
To Whom it may concern,  I was trying to get xgl to work on my on my one laptop.  I found this [http://doc.gwos.org/index.php/Installxgl](http://doc.gwos.org/index.php/Installxgl)
This actualy made it work but I soon realized that my computer is way to slow and old to handle all the stuff id like it to do.  I would like to know if there is any way that i can turn it off or reverse this.  I have tried deleting the stuff I added.  Please give me any information you can.  Thankyou

---

### Post by hokutonoken on 2006-11-20
Hello reis682,
to disable xgl just delete all the lines you added in /etc/gdm/gdm.conf-custom

Just open up a terminal window and invoke "gksudo gedit /etc/gdm/gdm.conf-custom"

You have to delete this very part

[servers]

# Override display 0 to use Xgl.
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/local/bin/Xgl :0 -fullscreen -ac -accel xv -accel glx:pbuffer
flexible=true

Save it.Then xgl won't bother you anymore.

Notice saving backup copies of config files is always recommended
If you had saved a copy of your old gdm.conf-custom now you would have been able to enable it again by simply renaming it.

Afterwards, if you modified your .Xsession file, you have to delete the lines you added to stop compiz from trying to start each time you begin a session.

Run "gksudo gedit .Xsession", delete all HOWTO's lines (those you added, of course) and save it.

Then invoke "chmod +x .Xsession" and you are done.

If you added a line in Sessions > Startup Programs (that was the recommended way, IMHO), just delete it.
 
Finally, you can delete XGL and compiz packages to free up some space on your hard drive.

Open up Synaptic and find xserver-xgl and all compiz packages, and remove them.

Hope this will help you.

---

