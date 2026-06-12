---
title: "E520n w/Nvidia 7300LE Ubuntu preinstalled - 3d is a bust"
date: 2007-06-05
forum: Dell  Ubuntu Support
---

### Post by doublecheese on 2007-06-05
I've tried everything.  From Restricted Device to Synaptic to using the command line.  I've tried nvidia-glx. I've tried nvidia-glx-new. I've removed all traces of nvidia.  I've tried Automatix.  I've done a clean install and tried restricted device manager.  I've written the generated xconfig files.  I've created xconfig files of my own.  I've turned on frame buffering.  It all leads to the same thing:  As soon as xserver tries to start, I get a blank screen and my monitor's built in hardware controls show on the screen with a message "Nn Valid Signal".  I've gone through all the ubuntu support documentation that exists.  I've searched this forum.  I've searched google.  I've tried every suggested method to get either the nvidia-glx and or the nvidia-glx-new driver to work.  I've config'ed x.  I've tried 3rd party support.  I've done a fresh reinstall.  I'm stumped.

This is the first experience I've had with linux.  I have most experience with Mac OS inculding Mac OSX.  I am familiar with UNIX.  I bought a Dell Dimension E520 with 1.8ghz core 2 duo, 250M drive, 1GB RAM, 256MB Nvidia Geforce 7300LE, DVD burner, Ubuntu pre-installed, and I'm trying to connect to a Nokia Multigraph 445Xpro CRT.  Nothing I do will get the nvidia 3D drivers to work.  I've spent 25+ hours on this problem since Saturday.  Only the nv drivers work.  I went to the Linux on Dell wiki [http://linux.dell.com/wiki/index.php/Wiki_Main_Page]("http://linux.dell.com/wiki/index.php/Wiki_Main_Page")

They do not even have my E520n system on file.  Any help is appreciated in getting 3d support working here.  Other than 3D I have not had any problems with ubuntu so far and I would like to keep it.  I would also like 3D support for my factory DELL card too:)  I like linux.  I really do.  I even want to put a Tux sticker on my car.  From the weekend I've had this box I will say that if I can get the 3D nvidia drivers to work I will be a linux user for life!

Any help is appreciated.  Thanks.

---

### Post by mifi on 2007-06-05
> **doublecheese said:**
> I've tried everything. 


Sounds like the card is not working properly.

This might be a very stupid suggestion, but have you checked in the box that you actually have received a machine with the nVidia card installed?
The standard E520 comes with a ATI card.

m

---

### Post by tseliot on 2007-06-05
If you want we can try to diagnose the error:

Install the nvidia driver again

Boot with the "nv" driver in your xorg.conf

Then (after Ubuntu has booted) Set the driver to "nvidia" in your /etc/X11/xorg.conf
Log out and Press CTRL+ALT+F1

You will get to the command line (no GUI)
Type:

```
sudo /etc/init.d/gdm stop (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm stop (if you use KDM)
```

Then:
```
startx -- -verbose 5 -logverbose 5
```

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C (select NO if it asks you if you want to see the output of the error or something like that)

Then type this in order to copy the output of the error to your home folder:
```
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
```
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
```
sudo nano /etc/X11/xorg.conf
```
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
```
sudo /etc/init.d/gdm restart (if you use GDM)
```
OR
```
sudo /etc/init.d/kdm restart (if you use KDM)
```


Post the content of that file (which you can find under /home/your_username/Xorg.0.log )

---

### Post by jarocooke on 2007-06-05
> **doublecheese said:**
> It all leads to the same thing:  As soon as xserver tries to start, I get a blank screen and my monitor's built in hardware controls show on the screen with a message "Nn Valid Signal". 

If the xserver was failing to start you would get a blue (mostly) text based screen asking if you want to see the xserver output, as it doesn't sound like this is happening, I would suspect that the driver is loading and working properly, but the monitor can't display the output, probably because the vertical and horizontal refresh rates are set wrongly.

My suggestion would be to get out the monitor manual and set the V & H refresh rates in /etc/X11/xorg.conf using the command sudo nano /etc/X11/xorg.conf

Then restart the xserver and see if it works properly.

BTW, if you can hear the startup "music" coming out of the speakers, but there is no signal going to the monitor, then the xserver is starting up properly, but the monitor can't display the signal.

The only other possibility is that the xorg.conf file might have an option in it forcing the xserver to output to an LCD instead of CRT, sorry can't remember what the option is, I have it at home though, so may update this later.  As a careat, this last sentence may be just laptop specific, I don't really know.

Good luck (we'll get to the bottom of it eventually, just hang in there).

---

### Post by magicfab on 2007-06-05
> **doublecheese said:**
> I've tried everything. [...]Any help is appreciated.  Thanks.

Did you buy Ubuntu support and if yes, what happened when you called ? Automatix is not included in any official support BTW.

I see several reports of people with your system and everything including 3d working, don forget to check Dell's wiki which lists known issues at the end of its page:
[http://linux.dell.com/wiki/index.php/Ubuntu_7.04](http://linux.dell.com/wiki/index.php/Ubuntu_7.04)

---

### Post by doublecheese on 2007-06-05
OK guys thanks for the help!  I do hear the chime of the ubuntu login screen so xserver must be working.  I am sorry if I cannot get too deep into the problem this morning as I am out the door on my way to work at the moment.  I will attempt to read on this problem more while at work today.  When I get home tonight I'll jump back into this little project.  

BTW I also thought perhaps this was a monitor issue.  I have no paperwork for this display as I literally saved it from being tossed in a dumpster!  I plan to get a new digital display very soon.  In the back of my mind I was thinking perhaps the display was the culprit however it works just fine with the nv drivers and I have no problem mirroring my powerbook to it.  

Thank you all for the suggestions.  I will try them tonight.  I'm feeling lucky today!

ALSO yes I do have the card in my machine.  I can see it through the slots in the case :)

---

### Post by jarocooke on 2007-06-05
```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	28-64
	Vertrefresh	43-60
EndSection
```

Sounds like it is almost certainly a refresh rate problem.  Unfortunately I have been unable to find the refresh rates on the internet, though to be honest I am not the best internet researcher I have ever found.  Just adapt the monitor section of your xorg.conf file (mine is above - for a laptop though!) to whatever you manage to find on the net and have a go. 

HOWEVER, some older monitors respond very badly (die permanently), when they receive incorrect refresh rates, so play at your own risk!!!

Hold on, just had another go with google and this may be of help - 

```

I run my 21" at 1280x1024@103Hz (this is at work)
And at home my 21" is at 1024x768@75Hz (this is because it can't do any better)
```

This came from the link below.

[http://www.techimo.com/forum/printthread.php?threadid=60647](http://www.techimo.com/forum/printthread.php?threadid=60647)

The Horizontal (above is the Vertical) can be calculate from the following I think (from wikipedia).
[http://en.wikipedia.org/wiki/Horizontal_scan_rate](http://en.wikipedia.org/wiki/Horizontal_scan_rate)

```

1280 x 1024 a (vertical) refresh rate of 96,000 / 1024 x 0.95 = 89Hz (rounded down)
```

If you calculate the rates for your target resolution and then enter sensible ranges that include these figures it may work.  In the past I have found the best thing to do is to err on the side of low rates rather than high rates.  So if you are feeling lucky you could just lower the bands a bit in xorg.conf and have a go.

Good luck and remember, if you toast your monitor, I warned you (though I have to say, I would probably give it a go anyway, but then I like to live on the wild side;)).

I don't suppose someone that actually knows something about CRT monitor refresh rates could lend a hand (in case you could guess I am not exactly an expert on the subject).

Actually it might be helpful if you posted your xorg.conf monitor section, maybe the rates in there are originally set up for an LCD display and your CRT isn't recognized, so the rates aren't updated to something more sensible.

---

### Post by jarocooke on 2007-06-05
Oooh!

Check this forum posting and also the link.

[http://ubuntuforums.org/showthread.php?t=435287](http://ubuntuforums.org/showthread.php?t=435287)
(The posting by SD_-Plissken - 2nd posting in thread)

[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

I am guessing this is pretty much what you want to do!!!

Good luck, let me know if you get it working.
:popcorn:

BTW I would only change the default colour depth as a last resort (Beryl and Compiz require a colour depth of 24 :D)

---

### Post by doublecheese on 2007-06-05
OK I'm home now and ready to try and diagnose this.

The first thing I will do is what tseliot recommended and I will post the error report here.

Also thank you jarocooke for the sleuth work you did.  I had a chance to skim over it while at work.  It seems like an interesting possibility however there are a few things that I do not understand.  If it is the refresh rate, why does the nv driver work but the nvidia driver not?  I have gone through custom configuration for the nv driver and chose the default refresh rates and they worked fine.  I try the same thing with the nvidia drivers and they don't work.  Each config has the same settings except for the driver!

I'll be posting again soon....

Also, to answer magicfab's question, I do not think I purchased Ubuntu support.  Honestly this is the only issue I've had with Ubuntu.  Everything else has been a pure pleasure :)

---

### Post by doublecheese on 2007-06-05
OK I did exactly as tseliot wrote.  The results:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux notamac 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  5 22:04:04 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Nokia 445Xi+"
(**) |   |-->Device "nVidia Corporation GeForce 7300 LE"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/X11R6/lib/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/X11R6/lib/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1028,01dd rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d1 card 1028,0405 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7300 LE rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xde000000/24, BIOS @ 0xdfe00000/17
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
(II) Active PCI resource ranges:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
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
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[21] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly. 
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
```

---

### Post by doublecheese on 2007-06-06
OK the configuration on my previous post did not bring the "Nn Valid Signal" message.  This post is after a complete system restore!  I did fresh install, snagged the updates from Update Manager, rebooted.  After reboot I ran Restricted Device Manager and enabled the nvidia drivers.  Rebooted and got the blank screen with the "Nn Valid Signal" message from my monitor.  I then followed the directions from tseliot's earlier post.  Here are the results:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux dell 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  5 23:37:36 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Nokia 445Xi+"
(**) |   |-->Device "nVidia Corporation GeForce 7300 LE"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1028,01dd rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d1 card 1028,0405 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7300 LE rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xde000000/24, BIOS @ 0xdfe00000/17
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
(II) Active PCI resource ranges:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
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
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[21] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.49.09
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) NVIDIA(0):     Nokia 445Xi+ (CRT-0)
(--) NVIDIA(0): Nokia 445Xi+ (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (104, 105); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[8] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[9] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[10] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[11] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[12] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[13] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[24] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

Any ideas?

---

### Post by tgalati4 on 2007-06-06
Couple of things to try:

Did you use nvidiaconfig (I'm writing this from a Mac so I don't have a machine to test) to write an initial xorg.conf?  You want to merge your original xorg.conf with the one created by the nvidia configuration script.

Lower your default resolution to something low (like 1024 by 768) and 16-bit color.  Edit your xorg as needed to make this happen.  Then test for 3D rendering.  Also stretch the vertical and horizontal refresh rates in your display section.  Most modern monitors will autosync.  Don't restrict yourself as this can be a problem getting 3D to work.

Post the output of:

glxgears -printfps

If you get 3D to work at this lower resolution, then start marching up the resolution and the color-bitrate until it breaks again.

---

### Post by dmb on 2007-06-06
That last log you gave tells us the server is running properly. It looks to me you have an invalid resolution/refresh rate in /etc/X11/xorg.conf.  Please refer to [http://ubuntuforums.org/showthread.php?t=435287](http://ubuntuforums.org/showthread.php?t=435287) and change accordingly. Start with the lower resolution and lower refresh rates first, and work your way up to find the suitable configuration for your older monitor. 

Also, the reason why nv didn't bug out is probably because the refresh rates/resolution won't/can't work with the nv driver, but do with nvidia, so when the nvidia driver is able to set them, your monitor yells at you.

---

### Post by jarocooke on 2007-06-06
The reason I figure that it is the refresh rate, is that I have had the same issue with an old CRT monitor that I used about two years ago.

As recommended above I would:

1. Try the nvidiaconfig script as suggested
2. Try widening the refresh rate band
3.  Go to the post by SD-Plissken ([http://ubuntuforums.org/showthread.php?t=435287](http://ubuntuforums.org/showthread.php?t=435287)) and follow those instructions.

If none of the above work,
4.  Lower the resolution
5.  Lower the colour depth

However if I was a betting man, I would say that it should be working fine, by the time you've done suggestion 3 above, if not sooner.

---

### Post by doublecheese on 2007-06-06
Hello I'm back again.  This time I did as dmb and others have suggested and altered my resolution!  I did exactly as the link in dmb's post said except I forgot to change nv to nvidia.  I started back up with the nv drivers but with the altered resolution and refresh rates as suggested in the link provided by dmb.  The nv drivers work fine but altering that file changed my monitor settings.  The screen became very painful to look at and there was/is a very large black bar at the left side of the screen.  It is not blocking any of the GUI or imposing upon the work area.  It just shrunk everything a little.  After realizing that I never changed the x config to read nvidia instead of nv, I made the appropriate changes and saved.  I then shut down because restart hangs the machine (yes I have read the cause and am aware of the problem and know the fix but I just did a clean install so the fix doesn't work cause I haven't applied it yet.....).  I boot back up with the correct nvidia drivers selected in the xconfig and boom, "Nn Valid Signal".  So I run the steps suggested by tseliot AGAIN and get this:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux dell 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  6 00:46:03 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Nokia 445Xi+"
(**) |   |-->Device "nVidia Corporation GeForce 7300 LE"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1028,01dd rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d1 card 1028,0405 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7300 LE rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xde000000/24, BIOS @ 0xdfe00000/17
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
(II) Active PCI resource ranges:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
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
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[21] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.49.09
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) NVIDIA(0):     Nokia 445Xi+ (CRT-0)
(--) NVIDIA(0): Nokia 445Xi+ (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (104, 105); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[8] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[9] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[10] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[11] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[12] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[13] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[24] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

I guess my question is:  Would all my problems go away if I bought a new LCD?

---

### Post by doublecheese on 2007-06-06
> **jarocooke said:**
> The reason I figure that it is the refresh rate, is that I have had the same issue with an old CRT monitor that I used about two years ago.

As recommended above I would:

1. Try the nvidiaconfig script as suggested
2. Try widening the refresh rate band
3.  Go to the post by SD-Plissken ([http://ubuntuforums.org/showthread.php?t=435287](http://ubuntuforums.org/showthread.php?t=435287)) and follow those instructions.

If none of the above work,
4.  Lower the resolution
5.  Lower the colour depth

However if I was a betting man, I would say that it should be working fine, by the time you've done suggestion 3 above, if not sooner.

Doh!  The link dmb posted and yours are the same.  OK.  The thing that gets me is that when the xconfig wizard thing comes up, the refresh bands are well within tolerances for this monitor.  Previously I have stretched them (via the wizard) to the maximum tolerances stated by the wizard.  They were quite wide.  Anywhere from 30 up to 160 between horizontal and vertical.  I still got the same problem.  I'm quite novice on the refresh rate (and how the config handles it) but I just don't see how a band like that can be too narrow.

---

### Post by doublecheese on 2007-06-06
I ran 

```
sudo dpkg-reconfigure xserver-xorg -phigh
```

followed by

```
sudo nvidia-xconfig
```

Shut down.  Boot up.  Same problem.  New log.

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux dell 2.6.20-16-generic #2 SMP Wed May 23 01:46:23 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jun  6 01:17:18 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Nokia 445Xi+"
(**) |   |-->Device "nVidia Corporation GeForce 7300 LE"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1028,01dd rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:19:0: chip 8086,104c card 1028,01dd rev 02 class 02,00,00 hdr 00
(II) PCI: 00:1a:0: chip 8086,2834 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1028,01dd rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1028,01dd rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1028,01dd rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1028,01dd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2812 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1028,01dd rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1028,01dd rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,01d1 card 1028,0405 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,3), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xdcf00000 - 0xdcffffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7300 LE rev 161, Mem @ 0xdd000000/24, 0xc0000000/28, 0xde000000/24, BIOS @ 0xdfe00000/17
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
(II) Active PCI resource ranges:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[1] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[2] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[3] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[4] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[5] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[6] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[7] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[12] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[13] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[14] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[15] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[16] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[17] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[18] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[19] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[21] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[22] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
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
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
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
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[18] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[19] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[20] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[21] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[22] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[23] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[24] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[25] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[27] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[28] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[5] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[6] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[7] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[8] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[9] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[10] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[11] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[21] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[22] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[23] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[24] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[25] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[26] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[27] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[28] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[29] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[30] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[31] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7300 LE at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.49.09
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7300 LE at PCI:1:0:0:
(--) NVIDIA(0):     Nokia 445Xi+ (CRT-0)
(--) NVIDIA(0): Nokia 445Xi+ (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "720x400"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) NVIDIA(0): DPI set to (104, 105); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdffdab00 - 0xdffdabff (0x100) MX[B]
	[8] -1	0	0xff970000 - 0xff9707ff (0x800) MX[B]
	[9] -1	0	0xff980800 - 0xff980bff (0x400) MX[B]
	[10] -1	0	0xdffdc000 - 0xdffdffff (0x4000) MX[B]
	[11] -1	0	0xdffdac00 - 0xdffdafff (0x400) MX[B]
	[12] -1	0	0xdffdb000 - 0xdffdbfff (0x1000) MX[B]
	[13] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B]
	[14] -1	0	0xdfe00000 - 0xdfe1ffff (0x20000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[17] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000ece0 - 0x0000ecff (0x20) IX[B]
	[24] -1	0	0x0000fec0 - 0x0000fedf (0x20) IX[B]
	[25] -1	0	0x0000fe30 - 0x0000fe33 (0x4) IX[B]
	[26] -1	0	0x0000fe20 - 0x0000fe27 (0x8) IX[B]
	[27] -1	0	0x0000fe10 - 0x0000fe13 (0x4) IX[B]
	[28] -1	0	0x0000fe00 - 0x0000fe07 (0x8) IX[B]
	[29] -1	0	0x0000ff40 - 0x0000ff5f (0x20) IX[B]
	[30] -1	0	0x0000ff60 - 0x0000ff7f (0x20) IX[B]
	[31] -1	0	0x0000ff80 - 0x0000ff9f (0x20) IX[B]
	[32] -1	0	0x0000ff00 - 0x0000ff1f (0x20) IX[B]
	[33] -1	0	0x0000ff20 - 0x0000ff3f (0x20) IX[B]
	[34] -1	0	0x0000ecc0 - 0x0000ecdf (0x20) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
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
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
```

---

### Post by jarocooke on 2007-06-06
If the monitor isn't being detected correctly Ubuntu may simply be trying to use too high a refresh rate, within the band that you have set.

What resolution does your monitor go to, from the file below it looks like the xserver thinks it goes to 1600 x 1200!

At those resolutions you will have to give up a bit of refresh rate.  I think the graphics card is using too high a refresh rate for you monitor.

Maybe if you posted you xorg.conf that would be helpful.

---

### Post by doublecheese on 2007-06-06
I changed default depth to 16.  Same problem.  I tried setting it to 1024x768@75Hz.  I'd say that's pretty modest.  I used the modeline generator but I must have entered it wrong.  I got the xserver error with the log that said what I had entered was wrong.  I've spent 4 nights on this now.  Ugh.  This has been a pain in the butt like none other.  

If I go buy a Widescreen LCD will I have this same problem?

EDIT:  I'm going to bed too.  I guess tomorrow will make 5 nights spent on this.

---

### Post by jarocooke on 2007-06-06
As far as problems with LCD monitors, I can only speak from my own experience.

I have used an ACER ALxxxx 19" (1280x1024) monitor for a couple of years and with a variety of distributions and never had this problem.  I was using the digital connector instead of the VGA, though I have tried both and there were no problems with either.

If you do get a Widescreen monitor the only thing that you might need to do is to add the correct widescreen resolution to xorg.conf, however it should still work even with the wrong resolution, just the picture will be "squished".

I only had the exact problem that you are having with one CRT monitor and it was a hiddeously old model.  If I remember correctly SUSE (now openSUSE) correctly set up the monitor, but Ubuntu didn't.  From what I heard at the time SUSE is better at detecting and correctly setting up monitors than most other distributions.  In fact I think this may still be true as Ubuntu often needs manual intervention to get the aspect ratio (resolution) correct on widescreen monitors.

That said Ubuntu is a way better distro, IMHO.

Could you post your xorg.conf here and I will see if I can suggest anything?

---

### Post by jarocooke on 2007-06-06
Try these, starting at the top and working down.  I am fairly confident that one of them will do the job.

Also I found another post by someone with the what sounds like the same monitor as you "Nokia Multigraph 445Xpro", he didn't say if was CRT, but judging from the refresh rates in the post it must have been.  His monitor only goes up to a resolution of 1280x1024@114kHz.  **However the file that you posted above seems to indicate that the xserver thinks that your monitor goes to a resolution of 1600x1200!!!**  Make sure that you don't have this too high resolution listed in any of you xorg.conf display lines (for reference I have attached what the lines should look like at the bottom of the post).

Hopefully one of these will work, as I am fresh out of ideas if they don't, but do post your xorg.conf so some other eyes can check it, it is easy to miss something when you have been looking at it for 4/5 days straight! :)

BTW I am moving house tomorrow, so won't be able to follow up on this until Saturday probably, but I'd love to know if you get it going.

@ 95kHz
```

HorizSync       30.0-103.0
VertRefresh     56.0-96.0
# 1280x1024 @ 95.00 Hz (GTF) hsync: 102.79 kHz; pclk: 180.91 MHz
Modeline "1280x1024_95.00"  180.91  1280 1376 1520 1760  1024 1025 1028 1082  -HSync +Vsync

```

@ 96kHz
```

HorizSync       30.0-104.0
VertRefresh     56.0-97.0
# 1280x1024 @ 96.00 Hz (GTF) hsync: 103.87 kHz; pclk: 182.81 MHz
Modeline "1280x1024_96.00"  182.81  1280 1376 1520 1760  1024 1025 1028 1082  -HSync +Vsync

```

@114kHz
```

HorizSync       30.0-125.0
VertRefresh     56.0-115.0
# 1280x1024 @ 114.00 Hz (GTF) hsync: 124.72 kHz; pclk: 219.50 MHz
Modeline "1280x1024_114.00"  219.50  1280 1376 1520 1760  1024 1025 1028 1094  -HSync +Vsync

```

@ 75kHz
```

HorizSync       30.0-80.0
VertRefresh     56.0-75.0
# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync

```

```

	SubSection "Display"
		Depth		1
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
	        Modes	      	"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes	      	"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"

```

---

### Post by tgalati4 on 2007-06-06
You have to love the forums.  If these xorg.conf settings don't work, then perhaps there is a problem with the monitor.  It's possible that it is losing sync at the higher frequencies due to a bad capacitor.  It happens.

At least we gave it a thorough test.

Good luck.

ps:  I also agree that SUSE is a great distro for getting the most out of older video cards and monitors.  It's just missing a few things--like synaptic.

---

### Post by doublecheese on 2007-06-06
Goodmorning!

I have good news.  I have been able to get the nvidia drivers working with my monitor thanks to the information posted by jarocooke!  Thank you!  If I were there I'd grab a box and help you with the move :)

I entered:

```
HorizSync       30.0-80.0
VertRefresh     56.0-75.0
# 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
```

and 

```
SubSection "Display"
		Depth		1
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
	        Modes	      	"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes	      	"1280x1024_95.00" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_95.00" "1024x768" "800x600" "640x480"
```

Which allowed me to see the nvidia splash screen on boot!  It went straight in to 1024x768 with a refresh rate of 75Hz.  Jacking up the resolution gives an unusable refresh rate...like the kind that makes your head hurt from looking at the screen.  I'm also able to open nvidia-settings and am presented with a large number of options.  

I can use the monitor in its current setting but would hope that with a 256MB card I could run at a higher resolution.  I can't say I fully understand what's going on here but I do have a much better understanding than I did before I started.  Funny...this issue has been such a pain but I've had to do so much work on it that I can't think of any better way to familiarize myself with Linux.  

Thank you all for your help.  I consider the problem solved for now although I will continue to tinker on getting the highest resolution and refresh rate possible.  Thanks again for all your help and a special thanks to jarocooke for really going the extra mile.  

Have a nice day!

---

### Post by tgalati4 on 2007-06-07
Remember when using 3D that 256 MB gets used up quickly because of the backing stores, texture maps, and other settings so you may not be able to operate at full resolution and use 3D at the same time.

It would not surprise me if the nVidia cards supplied by Dell do not have the same capabilities as a retail version of the same chipset.  Sort of like OEM tires on a new car--half the tread of a replacement tire.  Or half-filled inkjet cartridges with a new printer.

---

