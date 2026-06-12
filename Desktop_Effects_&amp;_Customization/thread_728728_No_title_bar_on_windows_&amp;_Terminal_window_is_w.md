---
title: "No title bar on windows &amp; Terminal window is white"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by InfoTech on 2008-03-19
I had my 7.10 Ubuntu working fine, until one moment. I saw this [http://www.youtube.com/watch?v=xC5uEe5OzNQ](http://www.youtube.com/watch?v=xC5uEe5OzNQ) on YOUTUBE and I wanted to install same stuff on my comp, so I followed the install instructions I found on: [http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html](http://onlyubuntu.blogspot.com/2007/03/how-to-install-beryl-with-latest-nvidia.html)

After restart, the OS could not "detect" my video card, resolution was 800x600. After some fiddling around, I succeeded in the following:
my login screen is in low res
after i login i have normal res, but no title bars on windows & terminal window is white - cant use it
after switching Visual Effects to None in System -> Preferences -> Appearance, I got windows title bars back and terminal window working. 

Any clues? Ideas? Thanks for help!

---

### Post by chewearn on 2008-03-19
Do you have Ubuntu Feisty Fawn 7.04, or the latest Gutsy Gibbon 7.10?

By the way, Beryl is obsolete; you should use compiz fusion (already install by default in Gutsy).

What graphics card do you have?  Are you prompted to install Restricted Video Driver?

---

### Post by InfoTech on 2008-03-19
Well, i find this names quite confusing, so I prefer numbering. I have 7.10. Apparently, following the instructions I had caused a problem with the graphic card's driver. I have 7900 NVidia graphic card. If I remember correctly, I "updated the drivers to the latest version". It is this update after which i have problems. My guess is based on:
```

sudo apt-get install nvidia-glx

sudo nvidia-xconfig --add-argb-glx-visuals --composite
```

Disabling and enabling "restricted driver" caused system to remove ```
nvidia-glx
``` and to install ```
nvidia-glx-new
```
After the restart, I got the message that "Ubuntu is running in low-graphics mode" and that my "screen and graphic card could not be detected correctly".
Any ideas?

---

### Post by chewearn on 2008-03-19
Remove the driver:
```
sudo apt-get purge nvidia-glx
```Install this:
```
sudo apt-get install nvidia-glx-new
sudo nvidia-glx-config enable
```
Restart.  Then, try enable Appearance > Visual effects.

---

### Post by InfoTech on 2008-03-19
Unfortunately, not solved. Still in "Low -graphics mode"

---

### Post by InfoTech on 2008-03-19
Disabling the "restricted driver" enables high res, but no effects. Note that the driver was working before my experiment with the a/m installation.

---

### Post by InfoTech on 2008-03-19
Can anyone explain what actually 
```
nvidia-xconfig --add-argb-glx-visuals --composite
```
means and how I can remove any harmfull effect on my configuration?

---

### Post by chewearn on 2008-03-19
This command:
```
nvidia-xconfig --add-argb-glx-visuals --composite
```will add two things into the proper places in this file: /etc/X11/xorg.conf

> Option          "AddARGBGLXVisuals"     "True"
and> Option          "Composite"     "Enable"
AFAIK, these are required additions to the file.  You can edit this file by:
```
sudo gedit /etc/X11/xorg.conf
```It's basically the configuration file for the Xorg.  Make a backup of the file before you change it.

---

### Post by chewearn on 2008-03-19
Also, have you remove beryl and emerald-themes, which you install in the howto.  To remove:
```
sudo apt-get remove beryl emerald-themes
```


Also, remove the beryl repositories.

```
sudo gedit /etc/apt/sources.lst
```

Delete the line:
> deb [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) feisty main
 
 Then run:
 ```
sudo apt-get update
```

---

### Post by InfoTech on 2008-03-19
Did all that:

There are no 

Option "AddARGBGLXVisuals" "True"
Option "Composite" "Enable"

fields in the xorg.conf

Clearly, it is problem with the "protected" driver, but have no idea how or why.

---

### Post by chewearn on 2008-03-19
I'm running out of ideas.

One last try; enable restricted driver again, then reboot, and look into the log file:
/var/log/Xorg.0.log


It a long file; look for any error.  Or post the file here, so we can take a look as well.

If you can also post /etc/X11/xorg.conf

---

### Post by InfoTech on 2008-03-19
I found no errors, but I'll paste it here, along with the xorg.conf, so I hope we find something.

file /var/log/Xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux veselin-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 19 18:58:57 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Failsafe Monitor"
(**) |   |-->Device "Failsafe Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2810 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2820 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2825 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,0292 card 1458,342e rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 11ab,4364 card 1458,e000 rev 12 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00008000 - 0x00008fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf6ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[2] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[3] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
	[4] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[5] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[6] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xf90fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:4), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf7000000 - 0xf8ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7900 GS rev 161, Mem @ 0xf4000000/24, 0xe0000000/28, 0xf5000000/24, I/O @ 0x8000/7
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
	[0] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[11] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[12] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[13] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[14] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[33] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[11] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[12] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[13] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[14] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[33] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
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
	[4] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[20] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[37] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[39] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
(WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 01:00:0
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[20] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[37] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[39] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[20] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[21] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[22] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[38] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[39] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[40] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[41] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[42] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.113
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G71 Board - p455h8f 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(**) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: SAM  Model: 194  Serial#: 1112092985
(II) VESA(0): Year: 2006  Week: 3
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
(II) VESA(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@56Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): 1152x870@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VESA(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz
(II) VESA(0): Monitor name: SyncMaster
(II) VESA(0): Serial No: HMEA115118
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff004c2d940139314942
(II) VESA(0): 	0310010380261e782ade95a3544c9926
(II) VESA(0): 	0f5054bfef8081808140714f01010101
(II) VESA(0): 	010101010101302a009851002a403070
(II) VESA(0): 	1300782d1100001e000000fd00384b1e
(II) VESA(0): 	510e000a202020202020000000fc0053
(II) VESA(0): 	796e634d61737465720a2020000000ff
(II) VESA(0): 	00484d45413131353131380a202000c5
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) VESA(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) VESA(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) VESA(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) VESA(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) VESA(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) VESA(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) VESA(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) VESA(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) VESA(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) VESA(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) VESA(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(II) VESA(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(II) VESA(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(II) VESA(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(II) VESA(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	NumberOfImages: 10
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 14
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
	LinBytesPerScanLine: 100
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 800
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 6
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
	LinBytesPerScanLine: 128
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1024
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
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
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
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 160
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
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
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
	MaxPixelClock: 229500000
Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
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
	MaxPixelClock: 229500000
*Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1600
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
	MaxPixelClock: 229500000
Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 3200
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
	MaxPixelClock: 229500000
*Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2048
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
	MaxPixelClock: 229500000
Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
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
	MaxPixelClock: 229500000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
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
	MaxPixelClock: 229500000
Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
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
	PhysBasePtr: 0xe0000000
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
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 320
	XResolution: 320
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 320
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
	MaxPixelClock: 229500000
*Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
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
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 320
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
	MaxPixelClock: 229500000
*Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c3
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xe0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Failsafe Monitor: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): Failsafe Monitor: Using vrefresh range of 56.00-75.00 Hz
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0): Display dimensions: (380, 300) mm
(**) VESA(0): DPI set to (53, 50)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[20] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[21] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[22] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[38] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[39] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[40] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[41] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[42] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.113
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G71 Board - p455h8f 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xe0000000,0x10000000)
(II) VESA(0): virtual address = 0xa7a7f000,
	physical address = 0xe0000000, size = 268435456
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
```

file /etc/x11/xorg.conf
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Apr 16 20:37:13 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7900 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7900 GS]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by chewearn on 2008-03-19
Alright, I can't find anything wrong with xorg.conf.

But the Xorg.0.log is showing the logging of failsafe mode (using Vesa driver), so you couldn't see what error the nvidia driver was giving prior to that. 

You can see near the top of the file:
> (==) Using config file: "/etc/X11/xorg.conf.failsafe"
and later:
> (II) VESA: driver for VESA chipsets: vesa

What we need is the log where the nvidia driver failed load.  I'm not 100% positive, but that file could be /var/log/Xorg.0.log.old

---

### Post by InfoTech on 2008-03-20
The only file I found that mention NVidia is Xorg.20.log, and it say:

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux veselin-desktop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.20.log", Time: Thu Feb 28 21:14:05 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "SyncMaster"
(**) |   |-->Device "nVidia Corporation G71 [GeForce 7900 GS]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,29a0 card 1458,5000 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1458,a002 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,2845 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1458,5004 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1458,5004 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1458,5006 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2810 card 1458,5001 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2820 card 1458,b002 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1458,5001 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2825 card 1458,b002 rev 02 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 10de,0292 card 1458,342e rev a1 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1458,b000 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1458,b000 rev 02 class 01,01,85 hdr 00
(II) PCI: 04:00:0: chip 11ab,4364 card 1458,e000 rev 12 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00008000 - 0x00008fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf4000000 - 0xf6ffffff (0x3000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00006000 - 0x000060ff (0x100) IX[B]
	[1] -1	0	0x00006400 - 0x000064ff (0x100) IX[B]
	[2] -1	0	0x00006800 - 0x000068ff (0x100) IX[B]
	[3] -1	0	0x00006c00 - 0x00006cff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:3), (0,3,3), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
	[4] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[5] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[6] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[7] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xf9000000 - 0xf90fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:4), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xf7000000 - 0xf8ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x80000000 - 0x800fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00007000 - 0x000070ff (0x100) IX[B]
	[1] -1	0	0x00007400 - 0x000074ff (0x100) IX[B]
	[2] -1	0	0x00007800 - 0x000078ff (0x100) IX[B]
	[3] -1	0	0x00007c00 - 0x00007cff (0x100) IX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation GeForce 7900 GS rev 161, Mem @ 0xf4000000/24, 0xe0000000/28, 0xf5000000/24, I/O @ 0x8000/7
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
	[0] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[11] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[12] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[13] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[14] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[33] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[1] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[2] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[3] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[4] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[5] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[6] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[10] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[11] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[12] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[13] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[14] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[17] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[21] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[22] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[29] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[31] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[33] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
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
	[4] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[20] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[37] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[39] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  100.14.19  Wed Sep 12 14:48:02 PDT 2007
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  100.14.19  Wed Sep 12 14:14:20 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[16] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[17] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[20] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[27] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[28] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[29] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[34] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[35] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[36] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[37] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[38] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[39] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[5] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[6] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[7] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[8] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[9] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[10] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[20] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[21] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[22] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[23] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[30] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[31] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[38] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[39] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[40] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[41] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[42] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
	[43] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[44] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
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
(II) NVIDIA(0): NVIDIA GPU GeForce 7900 GS (G71) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.71.22.41.05
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7900 GS at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-0): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(WW) NVIDIA(0): No valid modes for "720x400"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024"
(II) NVIDIA(0):     "1280x960"
(II) NVIDIA(0):     "1152x864"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "832x624"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xf8000000 - 0xf8003fff (0x4000) MX[B]
	[8] -1	0	0xf9000000 - 0xf9001fff (0x2000) MX[B]
	[9] -1	0	0xf9106000 - 0xf91060ff (0x100) MX[B]
	[10] -1	0	0xf9105000 - 0xf91053ff (0x400) MX[B]
	[11] -1	0	0xf9100000 - 0xf9103fff (0x4000) MX[B]
	[12] -1	0	0xf9104000 - 0xf91043ff (0x400) MX[B]
	[13] -1	0	0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xf4000000 - 0xf4ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] 0	0	0x00008000 - 0x0000807f (0x80) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[25] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[26] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[27] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e80f (0x10) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[31] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[32] -1	0	0x0000dc00 - 0x0000dc03 (0x4) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[34] -1	0	0x00000500 - 0x0000051f (0x20) IX[B]
	[35] -1	0	0x0000fc00 - 0x0000fc0f (0x10) IX[B]
	[36] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[42] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[43] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[44] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[45] -1	0	0x0000c000 - 0x0000c01f (0x20) IX[B]
	[46] -1	0	0x00008000 - 0x0000807f (0x80) IX[B](B)
	[47] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[48] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1280x1024"
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
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
SetClientVersion: 0 9
```

---

### Post by InfoTech on 2008-03-20
Finally, I completely messed up my installation! :) Luckily, because I will install the OS from the scratch. Just one question, is it sufficient to copy my home folder, to keep evolution emails?

---

### Post by chewearn on 2008-03-20
Ok.  I have not used evolution, but I presumed the emails are kept in the home directory.

---

### Post by InfoTech on 2008-03-20
Thanks for your help anyway!

---

### Post by tmccleve on 2008-06-18
Another alternative to this is reseting your options to default.

System>Preferences>Advanced Desktop Effect Settings>Preferences>underneath the label "Profiles"

---

### Post by chewearn on 2008-06-18
> **tmccleve said:**
> Another alternative to this is reseting your options to default.

System>Preferences>Advanced Desktop Effect Settings>Preferences>underneath the label "Profiles"


[I]Old thread resurrected: "I'm alive!!!"
[/I]
Anyway, beside the point that the issue in this thread is no longer the issue, I'm also not sure what your post is referring to.

---

