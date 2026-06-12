---
title: "Adding Screen Resolutions"
date: 2009-03-20
forum: Desktop Environments
---

### Post by Flash72 on 2009-03-20
Hi

I just installed Ubuntu 8.10 on a computer which I plan on connection to my TV for watching movies.  The problem is that the resolution that my TV needs 1280x768 is not in the list.  

When I boot it up with the TV connected I get this error: No valid modes.  Screen found but none have a usable configuration.

After reading up on the forums most people seem to suggest editing the xorg.conf but me being a beginner to linux have no idea what to put in there so I was hoping someone could help me out.  Or if there are any other suggestions I'm all ears.

Currently there is not much in there

[I]Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"

EndSection[/I]

Thanks,

Flash

---

### Post by bigbencg on 2009-03-20
You can use xrandr from the terminal to play with resolutions to find the one that works best with your TV.  I have a 19" monitor connected to a KVM, X would automatically set my refresh rate at 85Hz which my monitor does not support.  I used xrandr to test resolutions and refresh rates.  Once you find a suitable combination you can set the values in xorg.conf

first find out what you have

```
xrandr -q
```

> bigben@8151-KUBU:~$ xrandr -q
Screen 0: minimum 800 x 600, current 1920 x 1200, maximum 1920 x 1200
default connected 1920x1200+0+0 0mm x 0mm
   1920x1200      50.0*    51.0
   1600x1200      52.0
   960x600        53.0
   800x600        54.0


In this case, my output is called default, you may see VGA, HDMI, LVDS, TMDS, or TV.  listed will be the autodetected resolutions.  You can add your resolution by 

```
xrandr --addmode HDMI 1280x768
```

Then test the resolution, rate is not required.

```
xrandr --output HDMI --mode 1280x768 --rate 60
```

These links may help as well with xrandr usage.

[http://ubuntuforums.org/showthread.php?t=1083258&highlight=xrandr](http://ubuntuforums.org/showthread.php?t=1083258&highlight=xrandr)
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

Reading the manual is always helpful

```
man xrandr
```

You can add the xrandr commands to a startup script to enable the resolution at startup.

---

### Post by Flash72 on 2009-03-23
Thanks for the reply :)

Ok this is what I get when I enter *xrandr -q*

```
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

```

Then I tried  *xrandr --addmode default 1280x768*

and I got this error
```

xrandr: cannot find mode "1280x768"
```

Am I doing something wrong?

I did figure out a way to do it but its not really ideal.  If I boot up with my monitor connected then change my resolution to 1360x768 which is not what I was after but its close enough and its already in the list.  Then I unplug my monitor and plug in the TV (my TV has VGA plug) it works.  But I don't really want to have to go through all that every time I boot up.

I thought that maybe it might have something to do with the error I get when I boot up - *Ubuntu is running in low graphics mode. No valid modes, screen found but none have a usable configuration"*  So I tried to add the mode when I booted up with the monitor and I got the same error.

Any suggestions on how I can add that resolution?

Thanks,

Flash

---

### Post by bigbencg on 2009-03-23
I am assuming the xrandr output you posted is after the switch and your TV is connected.  This definantely sounds like a detection issue, the X system is trying to query your TV for resolutions and is not being returned any information.  Resulting in some default resolutions listed.
> 
Ok this is what I get when I enter xrandr -q

Code:

Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0

Or is this just your TV connected initially?

Either way, you need to manually specify your resolution.  My example with the KVM switch was just that, the monitor was not being detected properly and I was not getting a proper resolution.  I had to manually enter the specs of the monitor into xorg.conf.  Below is my code, in italics are the lines I added.

```

Section "Monitor"
	Identifier	"Configured Monitor"
	[I]HorizSync	30-83
	VertRefresh	55-75[/I]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	[I]DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024_75.00"[/I]
	EndSubSection
EndSection
```

If you can find the Horizontal and Vertical Sync ranges, enter those under the monitor section, under the screen section I defined the color depth and screen resolution+refresh rate.

I suggested using xrandr because you can make changes to the display on the fly, try setting your resolution without using addmode.  I don't know what desktop you are using, probably Gnome?  You can either play with xrandr, or modify xorg.conf which would require restarting the X system or rebooting.

---

### Post by Flash72 on 2009-03-24
That xrandr output is when I boot up with the TV connected.  If I boot up with my monitor connected then I get a whole bunch of resolutions listed.

What you said about the TV not returning information when the x system queries it makes a lot of sense.

So I tried editing the xorg.conf with the following (changes are in bold)

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	[B]HorizSync	30-50	
	VertRefresh	58-62[/B]
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	[B]DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x768_60.00"
	EndSubSection[/B]
EndSection
```

But this did not do anything when I restart it still gets the errors when booting up and I still can't change the resolution to 1280x768

I think I'm using Gnome, is that the standard desktop that is installed by default?  I just did a standard install and have not changed it.

Any ideas why this did not work?

Thanks,

Flash

---

### Post by mysticaltopher on 2009-03-24
I need to do the same thing on a friends computer, he has a Nvidia TNT2 video card and Ubuntu 8.10 is not compatible with it.  The card isn't recognised and the best resolution I can choose is 800x600. I'll try editing the xorg.conf file tonight to add the new resolutions and get back with any helpful tips or bumps along the way....

---

### Post by mister_p_1998 on 2009-03-24
Can I use this to tell my pc to start up in 1280 X 1024 rather than 640 X 480, as it starts on a timer with the screen turned off and always comes up in low res.

Steve

---

### Post by bigbencg on 2009-03-24
mister_p_1998,
     That is the idea, xrandr can be used to make changes on the fly.  There are two ways to implement the changes.  I am using KDE on all of my computers, I don't know where Xsetup lies in a Gnome installation.  You can search for the file it you want to.  In my situation an entry in /etc/kde4/kdm/Xsetup was made, I added my xrandr command to that file to set my resolution at boot up.  Or the old way, from which I have read is not the recommended way these days, is to edit Xorg.conf.  Which works as well.  I have not tried using these commands without a monitor connected.  I will have to experiment with that.  I may also have to install Gnome on a computer I have laying around to find out the directory structure for Gnome.

Flash, how is your TV connected?  VGA, DVI??  If you are changing the type of video connection between devices this may be why your entries are not working.  You are binding the resolution changes to a particular output.  Just a thought.  I will do my best to replicate this issue, I am curious to know as well.  I have a HDTV that has both HDMI and 15-pin D-sub that I can experiment with.

---

### Post by Flash72 on 2009-03-24
My TV uses a VGA connection.

When I have been trying these things I have been booting up the computer with the TV connected and not changing it.

---

### Post by bigbencg on 2009-03-25
I think I have come up with a solution, with no promise of resolution.  No pun intended.

I connected one of my computers, running kubuntu 8.10 to my HDTV.  Then the fun began, the text for some reason was incredibly small and could not be read until I stumbled my way into system settings and changed my fonts to 20pt.  Anyway, I queried xrandr for detected outputs.

```
bdevoe001@bdevoe001-desktop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1360 x 768
VGA connected 1360x768+0+0 (normal left inverted right x axis y axis) 1010mm x 570mm
   1360x768       60.0*+   59.8
   1280x768       59.9
   1024x768       60.0     60.0
   800x600        60.3     60.0
   640x480        60.0     59.9
   720x400        70.1
TMDS-1 disconnected (normal left inverted right x axis y axis)
```

My TV returned a large number of outputs, so I thought I would try and add a HD resolution.  I tried numerous times to use addmode and newmode in xrandr which was leading me nowhere.  I did some more searching and came across a forum on another site that talked about a command called "gtf".  This command is used to generate a "modeline" that when added to xorg.conf will add a mode in the xrandr output.  So I tried it.  My TV supports Full 1080, so I proceeded to produce an output for that resolution.  I used 60 Hz in the example below, you may have to experiment with other refresh rates to find one that works.

```
bdevoe001@bdevoe001-desktop:~$ gtf 1920 1080 60
# 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
```

1920 being width, 1080 height, 60 being the refresh rate.

I then pasted the resulting two line code into xorg.conf under the monitor section.  By now I assume you know where the file is located and how to edit it.  My xorg.conf "Monitor" section looked as follows:

```
Section "Monitor"
	Identifier	"Configured Monitor"
# 1920x1080 @ 60.00 Hz (GTF) hsync: 67.08 kHz; pclk: 172.80 MHz
  Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection
```

Then it was necessary to reload the configuration file, and being lazy I just restarted the computer.  After logging back in and heading straight for terminal I again queried xrandr.

```
bdevoe001@bdevoe001-desktop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 1920 x 1920
VGA connected 1360x768+0+0 (normal left inverted right x axis y axis) 1010mm x 570mm
   1360x768       60.0*+   59.8
   1920x1080_60.00   60.0
   1280x768       59.9
   1024x768       60.0     60.0
   800x600        60.3     60.0
   640x480        60.0     59.9
   720x400        70.1
TMDS-1 disconnected (normal left inverted right x axis y axis)
```

Which looked much like it did before but BEHOLD, my 1920x1080 resolution was listed.  What to do next?  Try it!

```
xrandr --output VGA --mode 1920x1080_60.00
```

At which point my screen went blank and I received a message from the TV that the input was not supported.  But the important thing here is the command worked.  But this does highlight a danger with the command, there is no 15 second confirmation countdown that will revert back to the previous resolution.  So be prepared to type another command setting the resolution back to the one that worked or restart the computer.  If the command results in a setup that does not work, use gtf to produce another modeline with another refresh rate and try again.

Reading some other forums and posts, I even found a nearly four year old post here at ubuntuforums.org [http://ubuntuforums.org/showthread.php?p=129379#post129379]("http://ubuntuforums.org/showthread.php?p=129379#post129379"), that state you can still use xorg.conf to set the new resolution under the "Screen" section.  I did not try this myself since my new resolution was unsupported on the analog VGA input.  So give it a shot, it may work.  If not, you might try loading the xrandr command as listed below.

Back to my KVM example from earlier, I was having trouble with screen resolution and position.  Once I found a setup that worked I set, using xrandr, the output at startup in a file called Xsetup.  You should be able to do the same.  I am using KDE so my file is located at /etc/kde4/kdm/Xsetup, I believe in Gnome it will be located at /etc/gdm/Xsetup.  This way the resolution is sure to be set.  Simply add the xrandr command to the file and save.  This file should be loaded at X startup, which is before the graphical login screen.

I sure hope this helps and you can set your resolution.  If it doesn't, I have no clue what to try next.

Ben

---

### Post by mister_p_1998 on 2009-03-25
So how do I setup xorg.conf to force resolutions ONLY 1280 X 1024 and over?
Steve

---

### Post by bigbencg on 2009-03-25
xorg.conf is used to set a specific resolution on a specific output device and monitor.  I am not sure what you mean by resolutions 1280x1024 and over.

---

### Post by Flash72 on 2009-03-26
Ok I tried what you said.

This is what I put in xorg.conf

```
Section "Monitor"
	Identifier	"Configured Monitor"
 # 1280x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 80.14 MHz
  Modeline "1280x768_60.00"  80.14  1280 1344 1480 1680  768 769 772 795  -HSync +Vsync
EndSection
```

When I restarted I still got the same error boot.  I went to the terminal ran xrandr -q but the mode was not there.

I have a feeling that the reason its not working is because of the error I get while booting "Ubuntu is running in low graphics mode"  I think this means its not even using xorg.conf but using a failsafe file instead.  Here is a copy of the log files if it helps.

:0.log
```
5369 5332
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux flash-media 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Thu Mar 26 21:05:34 2009
(++) Using config file: "/etc/X11/xorg.conf.failsafe"

error setting MTRR (base = 0xd0000000, size = 0x007f0000, type = 1) Invalid argument (22)
5369 5332
cp: cannot stat `/etc/X11/xorg_conf': No such file or directory

```

xorg.0.log
```

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux flash-media 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 26 21:05:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82G33/G31 Express Integrated Graphics Controller rev 16, Mem @ 0xfe980000/0, 0xd0000000/0, 0xfe800000/0, I/O @ 0x0000dc00/0
(--) PCI: (0@0:2:1) Intel Corporation 82G33/G31 Express Integrated Graphics Controller rev 16, Mem @ 0xfe780000/0
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0xfeaf03b0 - 0xfeaf03bb (0xc) IS[B]
	[10] 0	0	0xfeaf03c0 - 0xfeaf03df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G33
(--) intel(0): Chipset: "G33"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xFE980000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 8128 kB
(II) intel(0): VESA VBE OEM: Intel(r)Q33/Q35/G33 Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)Q33/Q35/G33 Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): I2C bus "SDVOB DDC Bus" initialized.
(II) intel(0): Output TMDS-1 has no monitor section
(II) intel(0): SDVOB: device VID/DID: 02:3C.06, clock range 25.0MHz - 200.0MHz
(II) intel(0): SDVOB: 1 input channel
(II) intel(0): SDVOB: TMDS0 output reported
(II) intel(0): Current clock rate multiplier: 1
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

Any ideas on how to stop this error?

Flash

---

### Post by bigbencg on 2009-03-26
I do not personally, I cannot recreate that issue.  I did some searching and found a post with a similar area

[http://lists.opensuse.org/radeonhd/2007-10/msg00290.html]("http://lists.opensuse.org/radeonhd/2007-10/msg00290.html")

The complaint yields the same error you are receiving, and if you click the next link, it was said to have fixed it.  The error at least.

Edit:

I looked at the x-server output, it seems that your output connections are detected, but X does not see your monitor and is unloading the graphics drivers.  You mentioned before that connecting an actual computer monitor at startup then switching to your TV at least allows you to do something.  I don't know why X would not detect your TV, but until it does this will never work.  

> II) intel(0): SDVOB: TMDS0 output reported
(II) intel(0): Current clock rate multiplier: 1
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA disconnected
(II) intel(0): Output TMDS-1 disconnected
(WW) intel(0): Unable to find initial modes
(EE) intel(0): No valid modes.
(II) UnloadModule: "intel"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(EE) Screen(s) found, but none have a usable configuration.


The instructions I posted before detailing how to add a mode, was based on the fact that the monitor was detected and the drivers were loaded.  Those instruction would work to add the mode you want, but you would have to use the other monitor to boot and switch to the TV.  Which I understand is not ideal.

---

### Post by Flash72 on 2009-03-27
Oh well, thanks for all you help.

I will have to keep searching the net to see if I can find someone with a similar problem.  If I can't fix it I guess I will have to go back to windows:(

---

