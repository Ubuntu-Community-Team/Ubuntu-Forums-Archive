---
title: "Fluxbox: themes and fonts"
date: 2007-07-11
forum: Desktop Environments
---

### Post by saggio on 2007-07-11
Hi there, 

I'm currently in the middle of making my very first theme for Fluxbox, and I've ran into a little snag. I've been following this tutorial [http://tenr.de/howtos/style_fbox/style_fbox.html](http://tenr.de/howtos/style_fbox/style_fbox.html) to make my theme, but I can't seem to get the fonts I specified in my theme.cfg file to work! I know I have them installed, as I used a very nifty script on installing fonts that I found on the forums here, and they show up in GIMP. 

My font specifications look something like this:
```

menu.title.font: times-14:bold

```

Any ideas?

---

### Post by kerry_s on 2007-07-11
that look's fine to me.
where are your times fonts installed?
how come you just didn't> sudo apt-get install msttcorefonts
and have ms fonts system wide?

---

### Post by saggio on 2007-07-11
> **kerry_s said:**
> that look's fine to me.
where are your times fonts installed?
how come you just didn't> sudo apt-get install msttcorefonts
and have ms fonts system wide?

Ah, perhaps I misrepresented myself. I installed a number of individual fonts (in .ttf format) that I had using this script, which I found on these forums:

```
#!/bin/bash
#
# This script helps to install fonts
#
# Set your default font storage directory here
##DEFAULT_DIR="$HOME/fonts"
DEFAULT_DIR=`pwd`
# Set the default font installation directory here
DEFAULT_DEST="/usr/share/fonts/truetype/font-install"


# Don't edit anything below unless you know what you're doing.

echo "In which directory are the fonts?"
echo -n "[$DEFAULT_DIR] "
read DIR

echo
echo "What is the extention (without the dot) of the fonts?"
echo -n "[ttf] "
read EXT

echo
echo "Where should the fonts be installed?"
echo "DO NOT CHANGE THIS UNLESS YOU KNOW WHAT YOU'RE DOING!"
echo -n "[$DEFAULT_DEST] "
read DEST

if [ -z "$DIR" ]; then
    DIR="$DEFAULT_DIR"
fi

if [ -z "$EXT" ]; then
    EXT="ttf"
fi

if [ -z "$DEST" ]; then
    DEST="$DEFAULT_DEST"
fi

sudo -v
if [ $? != 0 ]; then
    echo "Unable to obtain the necessary privileges. Exiting..."
    echo -n "Press <Enter> to continue. "
    read WER
    exit $?
fi

echo
echo

if [ ! -d "$DIR" ]; then
    echo "Directory $DIR does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read SDF
    exit 2
fi

if [ ! -d "$DEST" ]; then
    echo "Directory $DEST does not exist. Exiting..."
    echo -n "Press <Enter> to continue. "
    read DFG
    exit 1
fi

echo "Copying fonts..."
cd "$DIR"

for i in *."$EXT"; do
    sudo cp -iv "$i" "$DEST"
done

echo
echo
echo "Updating the font cache..."
sudo fc-cache -fv

if [ $? != 0 ]; then
    echo "Error updating the font cache. Your fonts haven't been completely installed. Try running sudo fc-cache -fv manually. Exiting..."
    echo -n "Press <Enter> to continue."
    read FSF
    exit $?
fi

echo
echo
echo "Finished."
echo
echo "You will probably need to restart running programs to use the new fonts."
echo -n "Press <Enter> to exit. "
read WERT
exit 0
```

So, I used that script and the install went off without any problems, and the fonts (alfredo being the one I want to use in this fluxbox theme) appear in GIMP no problem. But they don't show up in fluxbox.

---

### Post by kerry_s on 2007-07-11
from the looks of it, it looks like it's installed, but not for X and fluxbox is a X-window-manager. gimp searches for fonts it can use. So that's double check.

gedit /var/log/Xorg.0.log

copy and paste that here.


I'm pretty sure it's not, but i still would like to see the log. so anyways i'm going to try to explain the fix.

you need to tell X where the fonts are.

gksu gedit /etc/X11/xorg.conf

where you see the fontpaths you need to add the path to your fonts.
Example:
/usr/share/fonts/truetype/(name of your font)

now you need to fix the fonts that you've installed so X can understand them.

cd /usr/share/fonts/truetype/(name of your font)

when your inside the fonts folder run these commands

sudo mkfontscale
sudo mkfontdir

now you need to restart X, logout and press ctrl+alt+backspace

check the Xorg.0.log to see if they where used or run xset -q in terminal and look under font path to see if it shows the path to your fonts.

if all is good run> sudo fc-cache -fv

good luck.

---

### Post by saggio on 2007-07-11
Okay, I did everything you said, but they still won't show up as fonts for fluxbox. 

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux isis 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Jul 11 19:31:37 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard1"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard0"
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
	/usr/share/fonts/truetype/alphamalemodern,
	/usr/share/fonts/truetype/aliens,
	/usr/share/fonts/truetype/alfredo,
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
(**) Option "Xinerama" "0"
(**) Extension "Composite" is disabled
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
(II) PCI: 00:00:0: chip 10de,00e1 card 1043,813f rev a1 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10de,00e0 card 1043,813f rev a2 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,00e4 card 1043,813f rev a1 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,00e7 card 1043,813f rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,00e8 card 1043,813f rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:05:0: chip 10de,00df card 1043,80a7 rev a2 class 06,80,00 hdr 00
(II) PCI: 00:08:0: chip 10de,00e5 card 1043,813f rev a2 class 01,01,8a hdr 00
(II) PCI: 00:0a:0: chip 10de,00e3 card 1043,813f rev a2 class 01,01,85 hdr 00
(II) PCI: 00:0b:0: chip 10de,00e2 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:0e:0: chip 10de,00ed card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0332 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:09:0: chip 1412,1724 card 1412,3630 rev 01 class 04,01,00 hdr 00
(II) PCI: 02:0b:0: chip 1106,3044 card 7fc8,d008 rev 80 class 0c,00,10 hdr 00
(II) PCI: 02:0c:0: chip 1095,3114 card 1043,8136 rev 02 class 01,04,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x000b (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc800000 - 0xfe8fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdc700000 - 0xec6fffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:14:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000bfff (0x2000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfeafffff (0x200000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV35 [GeForce FX 5900XT] rev 161, Mem @ 0xfd000000/24, 0xe0000000/27, BIOS @ 0xfe8e0000/17
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeaff400 - 0xfeaff7ff (0x400) MX[B]
	[1] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[2] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[3] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[4] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[5] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[27] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[28] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaff400 - 0xfeaff7ff (0x400) MX[B]
	[1] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[2] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[3] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[4] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[5] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[8] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[11] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[12] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[13] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[14] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[15] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[17] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[20] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[21] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[22] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[23] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[24] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[27] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[28] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
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
	[4] -1	0	0xfeaff400 - 0xfeaff7ff (0x400) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[7] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[8] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[9] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[32] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[33] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[34] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
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
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.11  Wed Jun 13 18:58:58 PDT 2007
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
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  100.14.11  Wed Jun 13 18:23:34 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
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
	[4] -1	0	0xfeaff400 - 0xfeaff7ff (0x400) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[7] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[8] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[9] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[18] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[19] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[23] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[26] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[27] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[28] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[29] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[30] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[31] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[32] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[33] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[34] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaff400 - 0xfeaff7ff (0x400) MX[B]
	[5] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[6] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[7] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[8] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[9] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[10] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[11] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[12] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[25] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[26] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[27] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[29] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[30] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[31] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[32] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[33] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[35] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[36] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[37] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Screen0" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT-0: 1280x1024 +0+0; CRT-0: 1280x960 +0+0; CRT-0: 1280x800 +0+0; CRT-0: 1280x768 +0+0; CRT-0: 1152x864 +0+0; CRT-0: 1152x768 +0+0; CRT-0: 1024x768 +0+0; CRT-0: 800x600 +0+0; CRT-0: 640x480 +0+0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5900XT (NV35) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.35.20.27.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5900XT at
(--) NVIDIA(0):     PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(0):     NEC MultiSync 75 (CRT-1)
(--) NVIDIA(0): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(0): NEC MultiSync 75 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Display Device found referenced in MetaMode: CRT-0
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "CRT-0:1280x1024+0+0"
(II) NVIDIA(0):     "CRT-0:1280x960+0+0"
(II) NVIDIA(0):     "CRT-0:1280x800+0+0"
(II) NVIDIA(0):     "CRT-0:1280x768+0+0"
(II) NVIDIA(0):     "CRT-0:1152x864+0+0"
(II) NVIDIA(0):     "CRT-0:1152x768+0+0"
(II) NVIDIA(0):     "CRT-0:1024x768+0+0"
(II) NVIDIA(0):     "CRT-0:800x600+0+0"
(II) NVIDIA(0):     "CRT-0:640x480+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (104, 113); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Disabling 32-bit ARGB GLX visuals.
(II) NVIDIA(1): Creating default Display subsection in Screen section
	"Screen1" for depth/fbbpp 24/32
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "CRT-1: 1280x1024 +0+0; CRT-1: nvidia-auto-select +0+0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce FX 5900XT (NV35) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 131072 kBytes
(--) NVIDIA(1): VideoBIOS: 04.35.20.27.00
(II) NVIDIA(1): Detected AGP rate: 8X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce FX 5900XT at
(--) NVIDIA(1):     PCI:1:0:0:
(--) NVIDIA(1):     Samsung SyncMaster (CRT-0)
(--) NVIDIA(1):     NEC MultiSync 75 (CRT-1)
(--) NVIDIA(1): Samsung SyncMaster (CRT-0): 400.0 MHz maximum pixel clock
(--) NVIDIA(1): NEC MultiSync 75 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(1): Display Device found referenced in MetaMode: CRT-1
(II) NVIDIA(1): Assigned Display Device: CRT-1
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "CRT-1:1280x1024+0+0"
(II) NVIDIA(1):     "CRT-1:nvidia-auto-select+0+0"
(II) NVIDIA(1): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(1): DPI set to (98, 108); computed from "UseEdidDpi" X config
(--) NVIDIA(1):     option
(==) NVIDIA(1): Disabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 0	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeaff400 - 0xfeaff7ff (0x400) MX[B]
	[7] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xfebffc00 - 0xfebffcff (0x100) MX[B]
	[10] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[11] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[12] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[13] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[22] -1	0	0x0000a400 - 0x0000a403 (0x4) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac03 (0x4) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b47f (0x80) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[29] -1	0	0x0000c400 - 0x0000c47f (0x80) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c80f (0x10) IX[B]
	[31] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[32] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[33] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[34] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[35] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[36] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[37] -1	0	0x00005040 - 0x0000507f (0x40) IX[B]
	[38] -1	0	0x00005000 - 0x0000503f (0x40) IX[B]
	[39] -1	0	0x00005080 - 0x0000509f (0x20) IX[B]
	[40] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "CRT-0:1280x1024+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) NVIDIA(1): Setting mode "CRT-1:1280x1024+0+0"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
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
SetClientVersion: 0 9
```

---

### Post by kerry_s on 2007-07-11
I see that X see's them there's no ww for them so that's good.


```
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	[B]/usr/share/fonts/truetype/alphamalemodern,
	/usr/share/fonts/truetype/aliens,
	/usr/share/fonts/truetype/alfredo,[/B]
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
```


so there still not showing up in your style?
can you post the style, maybe something is overiding it?

---

### Post by saggio on 2007-07-11
I'm still working on it, and beside the problems with the fonts I'm having, some of the colours don't go well together. But it ought to look pretty good when everything works properly! 

Here you go: 
```
# This is a theme for Fluxbox
#
# Menu
menu.bevelWidth: 4

menu.borderWidth: 3
menu.borderColor: #000000

menu.bullet: diamond
menu.bullet.position: right

menu.itemHeight: 14

menu.title: sunken gradient elliptic
menu.title.color: #A45042
menu.title.textColor: #DCC1A4
menu.titleHeight: 22
menu.title.justify: center

menu.frame: bevel1
menu.frame.justify: center
menu.frame.color: #732C20
menu.frame.textColor: #DCC1A4

menu.hilite.color: #A45042

# Fonts
menu.title.font: alfredo-20:bold
menu.frame.font: aliens-14
window.font: alfredo-14:bold
toolbar.clock.font: alphamalemodern-14:bold
toolbar.iconbar.focused.font: alfredo-14
toolbar.iconbar.unfocused.font: alfredo-14


# Toolbar
toolbar.bevelWidth: 4

toolbar.borderWidth: 3
toolbar.borderColor: #A45042

toolbar.height: 16

toolbar: sunken gradient elliptic
toolbar.color: #EBC1C5

toolbar.clock.borderWidth: 3
toolbar.clock.borderColor: #A45042
toolbar.clock.justify: center
toolbar.clock.textColor: #FFFFFF
toolbar.clock.color: #EBC1C5

toolbar.systray: sunken gradient elliptic
toolbar.systray.borderWidth: 3
toolbar.systray.borderColor: #A45042
toolbar.systray.color: #EBC1C5

toolbar.workspace: bevel1
toolbar.workspace.justify: center
toolbar.workspace.borderWidth: 3
toolbar.workspace.borderColor: #A45042
toolbar.workspace.color: #EBC1C5
toolbar.workspace.textColor: #FFFFFF

toolbar.button: sunken gradient elliptic
toolbar.button.color: #A45042
toolbar.button.pressed.color: #DBC0A3

toolbar.iconbar.empty: bevel1
toolbar.iconbar.empty.color: #DBC0A3

toolbar.iconbar.focused: bevel1
toolbar.iconbar.focused.justify: left
toolbar.iconbar.focused.borderWidth: 1
toolbar.iconbar.focused.borderColor: #A45042
toolbar.iconbar.focused.textColor: #FFFFFF
toolbar.iconbar.focused.color: #DCC1A4

toolbar.iconbar.unfocused: sunken gradient elliptic
toolbar.iconbar.unfocused.justify: left
toolbar.iconbar.unfocused.textColor: #DCC1A4
toolbar.iconbar.unfocused.color: #DBC0A3

# Window 
window.bevelWidth: 4
window.borderWidth: 3
window.borderColor: #A45042

window.title.height: 22

window.justify: center

window.label.focus: bevel1
window.label.focus.color: #A45042
window.label.focus.textColor: #FFFFFF
window.label.unfocus: sunken bevel1
window.label.unfocus.color: #DBC0A3
window.label.unfocus.textColor: #DCC1A4

window.button.focus: bevel1
window.button.focus.color: A45042
window.button.unfocus: bevel1
window.button.unfocus.Color: A45042

window.title.focus: bevel1
window.title.focus.color: #996B65
window.title.unfocus: sunken gradient elliptic
window.title.unfocus.color: #DBC0A3

window.handleWidth: 8
window.handle.focus: bevel1
window.handle.focus.color: #996B65
window.handle.unfocus: sunken gradient elliptic
window.handle.unfocus.color: #DBC0A3




# Rounded corners
menu.roundCorners: TopRight TopLeft BottomRight BottomLeft
window.roundCorners: TopRight TopLeft BottomRight BottomLeft
toolbar.shaped: true|false

```

---

### Post by kerry_s on 2007-07-12
hmm, i don't know looks fine to me. i just use 1 font.

```
*.font:				DejaVu-12
```

---

### Post by saggio on 2007-07-12
I'm an idiot! 

I had my overly file (which I didn't think to check until just now) overriding my style specific fonts. 

Thanks for all of the help, though! Now I can add even more fonts to my styles.

---

### Post by saggio on 2007-07-12
Okay, even though I've been messing around with my overlay file (it should be working...don't know why it isn't) I can't seem to get any of the fonts to work properly. 

Does anyone have any ideas?

---

