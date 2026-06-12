---
title: "Installation Issues"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Eau on 2005-04-21
Hello

I'm a windows user who is really interested in commencing a dual boot
with the Kubuntu distribution as I perceive it to be well receiving towards those just beggening to understand the unique interfaces and intricacies of Linux.

There is a rather large obstical for me to overcome before I can proceed, however.

I have to be able to install the bloody thing : )

After i downloaded the "Kubuntu-5.04-install-i386" ISO I burned it (at x4).
I am able to navigate through the initial installation sequence without fault
but as soon as the "Base Installation" step begins I receive an error that reads :

" Debootstrap Error   Couldnt Retreive 'Coreutils' "

I imagine this had something to do with the quality of the writting to the CDR
and thusly re burnt it with the exact same results.

I than downloaded from another mirror (Canadian Mirror)
and burned that ISO with the exact same results.

It would seem as through there is an issue not concerning the ISO or the mannor in which it is burnt, but rather an incongruency with the system itself.

Here are the specs for my machine.

Intel Celeron 2.0 Ghz
256 DDR Ram
40GB HDD (NTFS Filesystem)
Onboard Sound and Video
Windows XP Pro
Practically Fresh Format.

I realize that there is a chance that I downloaded 2 ISO that were Bunk
so i'm going to try it a third time. But I refuse to beleive it has something to do with how or at what speed it is burnt at (After testing various speeds and CDR's with the same results every time).

It seems to me that the issue is that the install is searching for something that's not there, or that the ISO itself is currupt.

I took the liberty of running the self diagnostic for the Disc and returned the following at 99%

./pool/restricted/l/linux-restricted-modules-2.6.10/nvidia-glx-1.0.7174-0ubuntu1_i386.deb

found to be currupt.

This was the case on both ISOs

If this is a known issue, or perhaps if anyone could foster some advice id' be greatly apreciative for any feedback by means of this Forum or an email to

[email]djeau@msn.com[/email]

Thanks : )

---

### Post by heimo on 2005-04-21
Hi!

Check the downloaded isofile with md5sum program (also for Windows):
[http://www.linuxiso.org/viewdoc.php/verifyiso.html]("http://www.linuxiso.org/viewdoc.php/verifyiso.html")

There's MD5SUMS in the directory you downloeded the iso from. Like this one:
[http://se.releases.ubuntu.com/5.04/MD5SUMS]("http://se.releases.ubuntu.com/5.04/MD5SUMS")

The MD5 sum on the line with same filename should match with the output of md5sum [isofilename]. That tells you your isofile is fine. If not, I'd try to use bittorrent to download it - I've seen one guy here who couldn't download iso file from any of the mirrors through http (because of proxy corrupted the file), but was able to download it using bittorrent.

Also - order the installation CD for free on [http://www.ubuntu.com/]("http://www.ubuntu.com/")

---

### Post by Eau on 2005-04-21
Thank you very much for such a  speedy response!   : )

Now, Initially I have ordered the "Official Ubuntu Installation Disc"
so I can expect to be up and running with Ubuntu in about 6 to 8 weeks.

My main idea was to receive KDE and Ubuntu in a nice tight pacakge because
my experience with Linux based systems is severely limited.

Although I'm sure changing to KDE from Gnome from a fresh Ubuntu install
is a pretty straight forward process  (I hope....)

Now I took your advice and Ran an MD5SUM bit check and guess what....

My ISO is a bit-for-bit Match to the Sum on the (Canadian) mirrors.

This leads me to only a couple conclusions...

1. My ISO (being a carbon Copy of the Mirror's Original file) was corrupt to begin with.

2.  My burner is degrading (highly doubtful, yet possible)

3. There is, indeed, a system wide failiure to recognize a certain factor during installation.

I'm running outta ideas gang!

Thank You for your support.

: )

P.S
I'm going to Burn the Ubuntu Installation ISO (the one Virgin to KDE) and see what I get . . .

---

### Post by Eau on 2005-04-22
UPDATE :

I've re downloaded the Ubuntu & Kubuntu ISO's 
I've authenticated them both using the MD5SUM Bit Sequence Method.
I've burned them both to CDR using "Burnatonce" (X4 Speed)

Everything seems fine on both discs except for when the base installation occurs
there's always a Debootstrap Error.

"corutils" always seems to bugger things up on both discs.

I've also tried ed_agamemnon's network setup for Ubuntu.
This also has the same effect with the Base Installer only with

"bdsultils'

Looks like i'll have to wait for the "real deal" discs in the mail : ('

---

### Post by heimo on 2005-04-23
Seems like others are having same problem:
[http://www.ubuntuforums.org/showthread.php?t=28700]("http://www.ubuntuforums.org/showthread.php?t=28700")

Check this post on that thread:
[http://www.ubuntuforums.org/showpost.php?p=144553&postcount=7]("http://www.ubuntuforums.org/showpost.php?p=144553&postcount=7")

If you search the forum with "Debootstrap Error" you'll find more. Maybe there's a solution to this problem (I'll be searching too).



 [http://www.ubuntuforums.org/showpost.php?p=137441&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=137441&postcount=2")
 panickedthumb:
> As far as why the install failed, that's something that we would need to see. Have you tried installing again? If you do try to install again, check virtual console #3 by pressing ctrl+alt+f3 and seeing what information it gives.


:!: wojtaliks solution:
[http://www.ubuntuforums.org/showthread.php?t=17860]("http://www.ubuntuforums.org/showthread.php?t=17860")

---

### Post by Eau on 2005-04-23
Alright, after more research and application of aquired techniques I have managed
to go beyond my original 6% marker where I always encountered my Debootstrap issue.

However, at 79% I am now faced with....

"Debootstrap Error : Unable to Install Kernel.....Kernel Package "Linux 386"

A 10GB Partition was created and subsequently formated by the Ubuntu Partitioner. An EXT3 FIlesystem was also made for this purpose.

I'll continue to investigate potential issues and known solutions.

Thanks for your support.

---

### Post by heimo on 2005-04-23
Hmm... This is a long shot, but you could try changing disk access mode in BIOS. There is usually options normal, large and LBA. This has sometimes helped me with similar problems - no debootstrap errors, but problems with partitions. However this may be dangerous for your data - I'm not sure what your Windows will say about changing that value.

---

### Post by Eau on 2005-04-23
Through some fortunate allignment of the planets (and the awesome support of the Ubuntu Community) I've successfully installed Ubuntu : )

Now to familarize myself with all the new termonlogies and applications...

---

### Post by heimo on 2005-04-23
Great!

Btw, here's a thread about ubuntu-geeks automation script. I haven't tried it, but feedback seems to be quite positive:
[http://www.ubuntuforums.org/showthread.php?t=22646&page=1&pp=40](http://www.ubuntuforums.org/showthread.php?t=22646&page=1&pp=40)

What was the solution to your installation problem? Was it the disk access mode setting in BIOS?

---

### Post by Eau on 2005-04-23
As a matter of fact, I simply downloaded the Ubuntu Install ISO, as opposed to the Kubuntu ISO, and the installation went off without a hitch.

This confirmed my initial hunch about the ISO...

Now I'm having an issue with Screen resolution...
im stuck in 800X600................ I need 1208X1024
Yet, there's only the one setting available. . .

the struggle continues!  : )

---

### Post by heimo on 2005-04-23
Oh dear. :D

[http://www.ubuntuforums.org/showthread.php?t=21984]("http://www.ubuntuforums.org/showthread.php?t=21984")

This is my template to begin diagnosing resolution related problems:
 > Can you attach your

    * /etc/X11/xorg.conf
    * /var/log/Xorg.0.log
    * output of command line command lspci
    * monitor manufacturer and model
    * video card manufacturer and model

If you don't know all of those, it's ok, probably plenty of information in the log file.



---

### Post by Eau on 2005-04-23
Thanks for all your help Heimo, you're very generous.

Now to the matter at hand. . .

I'm looking at an HP Pavilion MX70 which had no problems getting down
on a reso. of 1208X1204, my Graphics are handled by an onboard (integrated)
Intel graphics accelerater type thing.

*******************************Here's Xorg.conf*************************************

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
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"MX70"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"MX70"
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
EndSection

Section "DRI"
	Mode	0666
EndSection
************************************************************************************

---

### Post by Eau on 2005-04-23
X Window System Version 6.8.2 (Ubuntu 6.8.2-10 20050405154308 [email]root@terranova.warthogs.hbd.com[/email])
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686
Build Date: 05 April 2005
	Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Tue Apr 5 12:12:40 UTC 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 23 14:45:23 2005
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "MX70"
(**) |   |-->Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) Option "XkbRules" "xorg"
(**) XKB: rules: "xorg"
(**) Option "XkbModel" "pc104"
(**) XKB: model: "pc104"
(**) Option "XkbLayout" "us"
(**) XKB: layout: "us"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/lib/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/lib/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "unix/:7100,/usr/lib/X11/fonts/misc,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1,/usr/lib/X11/fonts/100dpi,/usr/lib/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2560 card 109f,3189 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2562 card 109f,3189 rev 01 class 03,00,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24c2 card 109f,3189 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 109f,3189 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 109f,3189 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 109f,3189 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 109f,3189 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 109f,3189 rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:02:0: chip 10ec,8139 card 109f,3189 rev 10 class 02,00,00 hdr 00
(II) PCI: 02:0a:0: chip 1274,5880 card 1274,2003 rev 02 class 04,01,00 hdr 00
(II) PCI: 02:0b:0: chip 13f6,0111 card 13f6,0111 rev 10 class 04,01,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe8100000 - 0xe81fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corp. 82845G/GL [Brookdale-G] Chipset Integrated Graphics Device rev 1, Mem @ 0xf0000000/27, 0xe8000000/19
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xec000000 from 0xefffffff to 0xebffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe8100000 - 0xe81000ff (0x100) MX[B]
	[1] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[2] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[3] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[4] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[7] -1	0	0x00002800 - 0x0000283f (0x40) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[10] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe8100000 - 0xe81000ff (0x100) MX[B]
	[1] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[2] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[3] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[4] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[5] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[6] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[7] -1	0	0x00002800 - 0x0000283f (0x40) IX[B]
	[8] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[9] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[10] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[11] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[12] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[13] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe8100000 - 0xe81000ff (0x100) MX[B]
	[6] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[7] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[8] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[14] -1	0	0x00002800 - 0x0000283f (0x40) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[17] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/X11R6/lib/modules/extensions/libdbe.a
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
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
(II) Loading extension FontCache
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "record"
(II) Loading /usr/X11R6/lib/modules/extensions/librecord.a
(II) Module record: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "i810"
(II) Loading /usr/X11R6/lib/modules/drivers/i810_drv.o
(II) Module i810: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "keyboard"
(II) Loading /usr/X11R6/lib/modules/input/keyboard_drv.o
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 915GM
(II) Primary Device is: PCI 00:02:0
(--) Chipset 845G found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe8100000 - 0xe81000ff (0x100) MX[B]
	[6] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[7] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[8] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[14] -1	0	0x00002800 - 0x0000283f (0x40) IX[B]
	[15] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[16] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[17] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[18] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[19] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[20] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe8100000 - 0xe81000ff (0x100) MX[B]
	[6] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[7] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[8] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[9] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[10] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[17] -1	0	0x00002800 - 0x0000283f (0x40) IX[B]
	[18] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[24] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[25] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/X11R6/lib/modules/libvbe.a
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) I810(0): Depth 24, (--) framebuffer bpp 32
(==) I810(0): RGB weight 888
(==) I810(0): Default visual is TrueColor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Integrated Graphics Chipset: Intel(R) 845G
(--) I810(0): Chipset: "845G"
(--) I810(0): Linear framebuffer at 0xF0000000
(--) I810(0): IO registers at addr 0xE8000000
(II) I810(0): 1 display pipe available.
(II) I810(0): detected 8060 kB stolen memory.
(II) I810(0): I830CheckAvailableMemory: 200700 kB available
(II) I810(0): Will attempt to tell the BIOS that there is 12288 kB VideoRAM
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(II) I810(0): Before: SWF1 is 0x00000108
(II) I810(0): After: SWF1 is 0x00000108
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): BIOS now sees 8000 kB VideoRAM
(--) I810(0): Pre-allocated VideoRAM: 8060 kByte
(==) I810(0): VideoRAM: 32768 kByte
(==) I810(0): video overlay key set to 0x101fe
(**) I810(0): page flipping disabled
(==) I810(0): Using gamma correction (1.0, 1.0, 1.0)
(II) I810(0): BIOS Build: 2759
(==) I810(0): Device Presence: disabled.
(==) I810(0): Display Info: enabled.
(II) I810(0): Broken BIOSes cause the system to hang here.
	      If you encounter this problem please add 
		 Option "DisplayInfo" "FALSE"
	      to the Device section of your XF86Config file.
(II) I810(0): Display Info: CRT: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV: attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: LFP (local flat panel): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: CRT2 (second CRT): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Display Info: TV2 (second TV): attached: FALSE, present: FALSE, size: (0,0)
(II) I810(0): Currently active displays on Pipe A:
(II) I810(0): 	CRT
(==) I810(0): Display is using Pipe A
(--) I810(0): Maximum frambuffer space: 32600 kByte
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/X11R6/lib/modules/libddc.a
(II) I810(0): VESA VBE DDC supported
(II) I810(0): VESA VBE DDC Level 2
(II) I810(0): VESA VBE DDC transfer in appr. 1 sec.
(II) I810(0): VESA VBE DDC read successfully
(II) I810(0): Manufacturer: HWP  Model: 503  Serial#: 1529
(II) I810(0): Year: 2002  Week: 42
(II) I810(0): EDID Version: 1.3
(II) I810(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) I810(0): Sync:  Separate
(II) I810(0): Max H-Image Size [cm]: horiz.: 32  vert.: 24
(II) I810(0): Gamma: 2.80
(II) I810(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) I810(0): First detailed timing is preferred mode
(II) I810(0): redX: 0.632 redY: 0.335   greenX: 0.295 greenY: 0.593
(II) I810(0): blueX: 0.143 blueY: 0.066   whiteX: 0.281 whiteY: 0.311
(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
(II) I810(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) I810(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) I810(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
(II) I810(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
(II) I810(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
(II) I810(0): Serial No: THLFP01529
(II) I810(0): Monitor name: MX70
(II) I810(0): Ranges: V min: 47  V max: 120 Hz, H min: 30  H max: 70 kHz, PixClock max 110 MHz
(II) I810(0): Using detected DDC timings
(II) I810(0): 	HorizSync 30-70
(II) I810(0): 	VertRefresh 47-120
(II) I810(0): Will use BIOS call 0x5f05 to set refresh rates for CRTs.
(--) I810(0): Maximum space available for video modes: 8000 kByte
Mode: 20 (132x25)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 25
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 21 (132x43)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 43
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 22 (132x50)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 50
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 23 (132x60)
	ModeAttributes: 0xf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 594
	XResolution: 132
	YResolution: 60
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 30 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 24
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 24
	LinNumberOfImagePages: 24
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

---

### Post by Eau on 2005-04-23
Mode: 31 (640x400)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 32 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 16
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 16
	LinNumberOfImagePages: 16
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 34 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 38 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1600
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 3c (1920x1440)
	ModeAttributes: 0x1b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1920
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 40 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 41 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 12
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 12
	LinNumberOfImagePages: 12
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 42 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 43 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 44 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 45 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 48 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 49 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

---

### Post by Eau on 2005-04-23
Mode: 4b (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 3200
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4c (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 15
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 10
	GreenMaskSize: 5
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 10
	LinGreenMaskSize: 5
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 4d (1920x1440)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 3840
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3840
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 50 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 52 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 54 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1280x1024,MX70) mode clock 132.751MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,MX70) mode clock 132.751MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,MX70) mode clock 132.751MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,MX70) mode clock 128.943MHz exceeds DDC maximum 110MHz
(WW) (1280x1024,MX70) mode clock 128.943MHz exceeds DDC maximum 110MHz
Mode: 58 (1280x1024)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*(WW) (1600x1200,MX70) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 195.84MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 190.247MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 190.247MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 160.833MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 148.759MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 148.759MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 148.759MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 148.759MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
(WW) (1600x1200,MX70) mode clock 111.703MHz exceeds DDC maximum 110MHz
Mode: 5a (1600x1200)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 6400
	XResolution: 1600
	YResolution: 1200
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 6400
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 5c (1920x1440)
	ModeAttributes: 0x9a
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0005b77
	BytesPerScanline: 7680
	XResolution: 1920
	YResolution: 1440
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xf0000000
	LinBytesPerScanLine: 7680
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
(II) I810(0): MX70: Using default hsync range of 30.00-70.00 kHz
(II) I810(0): MX70: Using default vrefresh range of 47.00-120.00 Hz
(II) I810(0): Not using mode "1024x768" (no mode of this name)
(II) I810(0): Not using mode "800x600" (no mode of this name)
(1024x768,MX70) mode clock 100000MHz exceeds DDC maximum 110MHz
(800x600,MX70) mode clock 100000MHz exceeds DDC maximum 110MHz
(II) I810(0): Increasing the scanline pitch to allow tiling mode (640 -> 1024).
(--) I810(0): Virtual size is 640x480 (pitch 1024)
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 60Hz refresh for mode "640x480" (50)
(--) I810(0): Display dimensions: (320, 240) mm
(--) I810(0): DPI set to (50, 50)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/X11R6/lib/modules/libxaa.a
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.2.0
	ABI class: X.Org Video Driver, version 0.7
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(==) I810(0): VBE Restore workaround: enabled.
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/X11R6/lib/modules/libshadow.a
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.2
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xe807ffff (0x80000) MS[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MS[B]
	[2] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[3] -1	0	0x00100000 - 0x0fffffff (0xff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe8100000 - 0xe81000ff (0x100) MX[B]
	[8] -1	0	0x10000000 - 0x100003ff (0x400) MX[B]
	[9] -1	0	0xe8080000 - 0xe80803ff (0x400) MX[B]
	[10] -1	0	0xec000000 - 0xebffffff (0x0) MX[B]O
	[11] -1	0	0xe8000000 - 0xe807ffff (0x80000) MX[B](B)
	[12] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[19] -1	0	0x00002800 - 0x0000283f (0x40) IX[B]
	[20] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[21] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[22] -1	0	0x00001860 - 0x0000186f (0x10) IX[B]
	[23] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[24] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[25] -1	0	0x00001800 - 0x0000181f (0x20) IX[B]
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
(II) I810(0): VESA VBE Total Mem: 8000 kB
(II) I810(0): VESA VBE OEM: Brookdale-G Graphics Chip Accelerated VGA BIOS
(II) I810(0): VESA VBE OEM Software Rev: 1.0
(II) I810(0): VESA VBE OEM Vendor: Intel Corporation
(II) I810(0): VESA VBE OEM Product: Brookdale-G Graphics Controller
(II) I810(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) I810(0): Before: SWF1 is 0x00000108
(II) I810(0): After: SWF1 is 0x00000108
(==) I810(0): Default visual is TrueColor
(II) I810(0): Allocated 128 kB for the ring buffer at 0x0
(II) I810(0): Allocating at least 512 scanlines for pixmap cache
(II) I810(0): Initial framebuffer allocation size: 3968 kByte
(II) I810(0): Allocated 4 kB for HW cursor at 0x7fff000
(II) I810(0): Allocated 16 kB for HW (ARGB) cursor at 0x7ffb000
(II) I810(0): Allocated 4 kB for Overlay registers at 0x7ffa000 (0x0c32c000).
(II) I810(0): Allocated 64 kB for the scratch buffer at 0x7fea000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) I810(0): [drm] loaded kernel module for "i915" driver
(II) I810(0): [drm] DRM interface version 1.2
(II) I810(0): [drm] created "i915" driver at busid "pci:0000:00:02.0"
(II) I810(0): [drm] added 8192 byte SAREA at 0xd0317000
(II) I810(0): [drm] mapped SAREA 0xd0317000 to 0xb7d72000
(II) I810(0): [drm] framebuffer handle = 0xf0020000
(II) I810(0): [drm] added 1 reserved context for kernel
(II) I810(0): Allocated 1920 kB for the back buffer at 0x7c00000.
(II) I810(0): Allocated 1920 kB for the depth buffer at 0x7a00000.
(II) I810(0): Allocated 32 kB for the logical context at 0x79f8000.
(II) I810(0): Allocated 24704 kB for textures at 0xfe7e0000
(II) I810(0): Updated framebuffer allocation size from 3968 to 3976 kByte
(II) I810(0): Updated pixmap cache from 512 scanlines to 514 scanlines
(II) I810(0): 0x82e5a98: Memory at offset 0x00020000, size 3976 kBytes
(II) I810(0): 0x86679e8: Memory at offset 0x07fff000, size 4 kBytes
(II) I810(0): 0x8667a10: Memory at offset 0x07ffb000, size 16 kBytes
(II) I810(0): 0x8646774: Memory at offset 0x00000000, size 128 kBytes
(II) I810(0): 0x82e5ad8: Memory at offset 0x07fea000, size 64 kBytes
(II) I810(0): 0x86423f0: Memory at offset 0x07ffa000, size 4 kBytes
(II) I810(0): 0x82e5b28: Memory at offset 0x07c00000, size 1920 kBytes
(II) I810(0): 0x82e5b48: Memory at offset 0x07a00000, size 1920 kBytes
(II) I810(0): 0x82e5b88: Memory at offset 0x079f8000, size 32 kBytes
(II) I810(0): 0x82e5b68: Memory at offset 0x00402000, size 24704 kBytes
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] Registers = 0xe8000000
(II) I810(0): [drm] Back Buffer = 0xf7c00000
(II) I810(0): [drm] Depth Buffer = 0xf7a00000
(II) I810(0): [drm] ring buffer = 0xf0000000
(II) I810(0): [drm] textures = 0xf0402000
(II) I810(0): [drm] dma control initialized, using IRQ 16
(II) I810(0): [drm] Initialized kernel agp heap manager, 25296896
(II) I810(0): [dri] visual configs initialized
(==) I810(0): Write-combining range (0xf0000000,0x8000000)
(II) I810(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x007df000 (pgoffset 2015)
(II) I810(0): xf86BindGARTMemory: bind key 0 at 0x07fff000 (pgoffset 32767)
(II) I810(0): xf86BindGARTMemory: bind key 1 at 0x07ffb000 (pgoffset 32763)
(II) I810(0): xf86BindGARTMemory: bind key 3 at 0x07fea000 (pgoffset 32746)
(II) I810(0): xf86BindGARTMemory: bind key 2 at 0x07ffa000 (pgoffset 32762)
(II) I810(0): xf86BindGARTMemory: bind key 4 at 0x07c00000 (pgoffset 31744)
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x07a00000 (pgoffset 31232)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x079f8000 (pgoffset 31224)
(II) I810(0): Before: SWF1 is 0x00000108
(II) I810(0): After: SWF1 is 0x00000108
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): Mode bandwidth is 18 Mpixel/s
(II) I810(0): maxBandwidth is 640 Mbyte/s, pipe bandwidths are 96 Mbyte/s, 0 Mbyte/s
(II) I810(0): LFP compensation mode: 0x1
(II) I810(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		21 128x128 slots
		5 256x256 slots
(==) I810(0): Backing store disabled
(==) I810(0): Silken mouse enabled
(II) I810(0): Initializing HW Cursor
(**) Option "dpms"
(**) I810(0): DPMS enabled
(II) I810(0): X context handle = 0x00000001
(II) I810(0): [drm] installed DRM signal handler
(II) I810(0): [DRI] installation complete
(II) I810(0): direct rendering: Enabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
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
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
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
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!

---

### Post by Eau on 2005-04-23
OY that's alot of information that i'm practically ignorant to. . .
I hope you can decipher something informative and practical to my current situation.

: )

---

### Post by heimo on 2005-04-23
The logfile would be very helpful. I couldn't find specification sheet for your monitor, so if you can check the horizontal and vertical refresh rate values from manual, it'd help. These are my best guesses. Are you sure you want to use 1280 x 1024? I think your monitor can only do 60Hz at that resolution, am I mistaken? For 1024x768 you should be able to get 85Hz which is much better in my opinion.

Well, anyway - I'd try to put something like this in the xorg.conf: (instructions how to edit the file are in the thread I mentioned earlier)

 ```
 Section "Monitor"
	Identifier	"MX70"
	Option		"DPMS"
	HorizSync	30-69
	VertRefresh 60-90
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"MX70"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes	    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

```

So, what I did was add two lines to Monitor section and remove unused subsections from Screen section and put "1280x1024" line in there for the highest supported resolution. If those will not work, you may need to add custom modelines (let's see that later, if neccessary).

---

### Post by heimo on 2005-04-23
Oh! Please do one thing. Edit those posts, select all the text and put code tags around them. # sign on this fancier post editor. Or just manually 

[ CODE ] 
    your long post here
[/ CODE ]

Don't put spaces in those tags, I had to so that the tags will be visible. This will put the long text in a nice scrollable window. There's a way to put files as attachments on this forum - I haven't had to do it yet, but I've seen it's possible - that'd be even better. :)

Thanks!

---

### Post by Eau on 2005-04-23
Sorry.

For the sake of a better reference, go to [http://cotamod.foreverstudios.com/djeau/](http://cotamod.foreverstudios.com/djeau/)
and you'll find the 2 files just chillin there.

---

### Post by heimo on 2005-04-23
Your automaticly detected HorizSync and VertRefresh values are fine. You don't need those two lines in Monitor section. (Wow, I'm quite proud how I guessed the HorizSync 30-69, the correct one is 30-70.) But you can experiment if there's difference if you have those lines or not (use # character in beginning of line to comment out / disable).

Instead you could put this line into Monitor section:
 ```
Modeline "1024x768"  94.50 1024 1072 1168 1376 768 769 772 808
``` 
I don't know if these will have any effect, but at least something to try. Make a backup of your config file before destroying it. :) Oh, and you need to restart X for changes to take effect. If the config file is broken, you'll end up in console without graphical user interface.

---

### Post by Eau on 2005-04-23
Should fixing these Configuration files wait, if i plan on switching to KDE?

---

### Post by heimo on 2005-04-23
No, the same Xorg will be there with KDE too.

---

### Post by Eau on 2005-04-23
arrgghh!

I'm still completely ignorant as to what to do to attempt to rectify my resolution problems. . .

I'll keep searching. . . 

(600x800 is giving my a terrible headache!)

---

### Post by heimo on 2005-04-23
Install all the updates:
System->Administration->UbuntuUpdateManager

Check these threads:
[http://www.ubuntuforums.org/showthread.php?t=28428&highlight=i810+resolution+stuck]("http://www.ubuntuforums.org/showthread.php?t=28428&highlight=i810+resolution+stuck")
[http://www.ubuntuforums.org/showthread.php?t=12958&highlight=i810+resolution+stuck]("http://www.ubuntuforums.org/showthread.php?t=12958&highlight=i810+resolution+stuck")

Especially this one:
[http://www.ubuntuforums.org/showthread.php?t=27029](http://www.ubuntuforums.org/showthread.php?t=27029)

---

### Post by Eau on 2005-04-24
I solved my problems by changing the "i810" driver to "vesa"

At login i experienced a glitchy kind of screen before the splash
but im willing to live with it if it persists...

hoorah.

---

### Post by heimo on 2005-04-24
[QUOTE=Eau]I solved my problems by changing the "i810" driver to "vesa"

At login i experienced a glitchy kind of screen before the splash
but im willing to live with it if it persists...

hoorah.[/QUOTE]

Great! Hopefully the issues with i810 and Kubuntu install CDs will be fixed in future. But at least you now have a working desktop. I with vesa driver would be some kind of automatic fallback if chipset specific (ie i810) driver fails.

:)

---

### Post by mrdibbler on 2005-04-27
[QUOTE=Eau]As a matter of fact, I simply downloaded the Ubuntu Install ISO, as opposed to the Kubuntu ISO, and the installation went off without a hitch.

This confirmed my initial hunch about the ISO...

Now I'm having an issue with Screen resolution...
im stuck in 800X600................ I need 1208X1024
Yet, there's only the one setting available. . .

the struggle continues!  : )[/QUOTE]
 Try a root terminal
then type  base-config

You should get to a part which allows you to set alternative screen resoloutions.

I think!  Anyhow let me know if that works.

---

