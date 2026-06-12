---
title: "Upgrade broke my X server. Please help."
date: 2009-05-26
forum: General Help
---

### Post by SkankinRatFink on 2009-05-26
Hey all. Using the Ubuntu Studio update manager, I went to update from 8.10 to 9.04. It seemed like it went through the update just fine, but when I rebooted, the X server won't start, and I get command line only. I really want to get my desktop back, so I hope you can help me. I have an nVidia GeForce 8400 GS.

When I boot up, this is what I get ...

> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Naturally, I took a look at the output, but I don't know what to make of it. If I view the output, I get:

(Eviscerateur is my hostname)

> X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux Eviscerateur 2.6.27-11-generic #1 SMP
Wed Apr 1 20:53:41 UTC 2009 x86_64
Build Date: 09 April 2009 02:11:54AM
xorg-server 2:1.6.0-0ubuntu14 (buildd@crested.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 26 19:32:56 2009
(==) Using config file: "/etc/X11/xorg.conf"
FATAL: Module nvidia not found.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): ***Aborting***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the X.Org Foundation support
at [http://wiki.x.org](http://wiki.x.org)
for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing log

"Failed to load the NVIDIA kernel Module" seems to me to be the likely culprit. I'm still a newbie at low-level Linux stuff like the kernel. I checked the X.org wiki and couldn't find anything that can help me, at my level of experience. I did try reinstalling the nVidia driver with Envy, which didn't work. Command line output from Envy:

> Error:

EnvyNG has detected that the headers for your kernel are missing and cannot be installed

I know there are some very smart people on this board who can probably guide me through this in a snap ... thanks in advance!

---

### Post by SkankinRatFink on 2009-05-27
Bump ... I would really like to get some help with this if I can ...

I don't want to resort to a clean install. :(

---

### Post by Bender2k14 on 2009-05-27
Can you post your /etc/X11/xorg.conf file?

---

### Post by SkankinRatFink on 2009-05-27
OK. /etc/X11/xorg.conf:

> Section "Screen"
[INDENT]Identifier "Default Screen"[/INDENT]
[INDENT]DefaultDepth 24[/INDENT]
EndSection

Section "Module"
[INDENT]Load "glx"[/INDENT]
EndSection

Section "Device"
[INDENT]Identifier "Default Device"[/INDENT]
[INDENT]Driver "nvidia"[/INDENT]
[INDENT]Option "NoLogo" "True"[/INDENT]
EndSection

---

### Post by SkankinRatFink on 2009-05-29
Bump ... does the xorg.conf help?

---

### Post by Bender2k14 on 2009-06-01
> **SkankinRatFink said:**
> Bump ... does the xorg.conf help?

Not sure yet.

How about posting the contents of "/var/log/Xorg.0.log" in case there is some "additional information" that is useful.

---

### Post by Bender2k14 on 2009-06-01
> **SkankinRatFink said:**
> Error:

EnvyNG has detected that the headers for your kernel are missing and cannot be installed

The following commands should install your kernel headers.

```
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by SkankinRatFink on 2009-06-02
> **Bender2k14 said:**
> The following commands should install your kernel headers.

```
sudo apt-get update
sudo apt-get install linux-headers-$(uname -r)
```

OK, shortest things first---- the update went fine, but the install command gave me this:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-2.6.27-11-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package linux-headers-2.6.27-11-generic has no installation candidate


And secondly ...

> **Bender2k14 said:**
> How about posting the contents of "/var/log/Xorg.0.log" in case there is some "additional information" that is useful.

Here is the entirety of Xorg.0.log:

> X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun  2 02:05:17 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation G80 [GeForce 8400 GS]"
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
(II) Loader magic: 0x81ea440
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1002,5956 card 1002,5956 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 1002,5978 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:04:0: chip 1002,597a card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:06:0: chip 1002,597c card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 1002,597d card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:12:0: chip 1002,4380 card 1043,81ef rev 00 class 01,06,01 hdr 00
(II) PCI: 00:13:0: chip 1002,4387 card 1043,8288 rev 00 class 0c,03,10 hdr 80
(II) PCI: 00:13:1: chip 1002,4388 card 1043,8288 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:2: chip 1002,4389 card 1043,8288 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:3: chip 1002,438a card 1043,8288 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:4: chip 1002,438b card 1043,8288 rev 00 class 0c,03,10 hdr 00
(II) PCI: 00:13:5: chip 1002,4386 card 1043,8288 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:14:0: chip 1002,4385 card 1043,8288 rev 14 class 0c,05,00 hdr 80
(II) PCI: 00:14:1: chip 1002,438c card 1043,8288 rev 00 class 01,01,8a hdr 00
(II) PCI: 00:14:2: chip 1002,4383 card 1043,8288 rev 00 class 04,03,00 hdr 00
(II) PCI: 00:14:3: chip 1002,438d card 1043,8288 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:14:4: chip 1002,4384 card 0000,0000 rev 00 class 06,04,01 hdr 81
(II) PCI: 00:18:0: chip 1022,1100 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:1: chip 1022,1101 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:2: chip 1022,1102 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 00:18:3: chip 1022,1103 card 0000,0000 rev 00 class 06,00,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0422 card 1682,2309 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,6121 card 11ab,6121 rev b1 class 01,01,8f hdr 00
(II) PCI: 03:00:0: chip 11ab,4364 card 1043,81f8 rev 12 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 11ab,6121 card 11ab,6121 rev b2 class 01,01,8f hdr 00
(II) PCI: 05:06:0: chip 109e,036e card 0000,0000 rev 11 class 04,00,00 hdr 80
(II) PCI: 05:06:1: chip 109e,0878 card 0000,0000 rev 11 class 04,80,00 hdr 80
(II) PCI: 05:08:0: chip 11c1,5811 card 1043,8294 rev 70 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:2:0), (0,1,1), BCTRL: 0x001b (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfe7fffff (0x4800000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:4:0), (0,2,2), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000bfff (0x2000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:6:0), (0,3,3), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:7:0), (0,4,4), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000efff (0x2000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:20:3), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:20:4), (0,5,5), BCTRL: 0x0003 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xf8f00000 - 0xf8ffffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0422) rev 161, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfa000000/25, I/O @ 0x9800/7, BIOS @ 0xfe7e0000/17
(--) PCI: (5:6:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xf8fff000/12
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe0000000 to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[1] -1	0	0xf8ffe000 - 0xf8ffefff (0x1000) MX[B]
	[2] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[3] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[4] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[5] -1	0	0xf9ff4000 - 0xf9ff7fff (0x4000) MX[B]
	[6] -1	0	0xf9fff000 - 0xf9fff0ff (0x100) MX[B]
	[7] -1	0	0xf9ffa000 - 0xf9ffafff (0x1000) MX[B]
	[8] -1	0	0xf9ffb000 - 0xf9ffbfff (0x1000) MX[B]
	[9] -1	0	0xf9ffc000 - 0xf9ffcfff (0x1000) MX[B]
	[10] -1	0	0xf9ffd000 - 0xf9ffdfff (0x1000) MX[B]
	[11] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[12] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B](B)
	[15] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[30] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[36] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[37] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[38] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[39] -1	0	0x00007000 - 0x00007003 (0x4) IX[B]
	[40] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[41] -1	0	0x00009800 - 0x0000987f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[1] -1	0	0xf8ffe000 - 0xf8ffefff (0x1000) MX[B]
	[2] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[3] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[4] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[5] -1	0	0xf9ff4000 - 0xf9ff7fff (0x4000) MX[B]
	[6] -1	0	0xf9fff000 - 0xf9fff0ff (0x100) MX[B]
	[7] -1	0	0xf9ffa000 - 0xf9ffafff (0x1000) MX[B]
	[8] -1	0	0xf9ffb000 - 0xf9ffbfff (0x1000) MX[B]
	[9] -1	0	0xf9ffc000 - 0xf9ffcfff (0x1000) MX[B]
	[10] -1	0	0xf9ffd000 - 0xf9ffdfff (0x1000) MX[B]
	[11] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[12] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[13] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[14] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B](B)
	[15] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[16] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[19] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[20] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[22] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[27] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[28] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[30] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[34] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[35] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[36] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[37] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[38] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[39] -1	0	0x00007000 - 0x00007003 (0x4) IX[B]
	[40] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[41] -1	0	0x00009800 - 0x0000987f (0x80) IX[B](B)
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
	[4] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[5] -1	0	0xf8ffe000 - 0xf8ffefff (0x1000) MX[B]
	[6] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[7] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[8] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[9] -1	0	0xf9ff4000 - 0xf9ff7fff (0x4000) MX[B]
	[10] -1	0	0xf9fff000 - 0xf9fff0ff (0x100) MX[B]
	[11] -1	0	0xf9ffa000 - 0xf9ffafff (0x1000) MX[B]
	[12] -1	0	0xf9ffb000 - 0xf9ffbfff (0x1000) MX[B]
	[13] -1	0	0xf9ffc000 - 0xf9ffcfff (0x1000) MX[B]
	[14] -1	0	0xf9ffd000 - 0xf9ffdfff (0x1000) MX[B]
	[15] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[16] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[17] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[18] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B](B)
	[19] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[20] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[21] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[35] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[36] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[42] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[43] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[44] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[45] -1	0	0x00007000 - 0x00007003 (0x4) IX[B]
	[46] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[47] -1	0	0x00009800 - 0x0000987f (0x80) IX[B](B)
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
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
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
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.5
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
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, GeForce 8700M GT,
	Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M,
	Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce 8400 GS found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[5] -1	0	0xf8ffe000 - 0xf8ffefff (0x1000) MX[B]
	[6] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[7] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[8] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[9] -1	0	0xf9ff4000 - 0xf9ff7fff (0x4000) MX[B]
	[10] -1	0	0xf9fff000 - 0xf9fff0ff (0x100) MX[B]
	[11] -1	0	0xf9ffa000 - 0xf9ffafff (0x1000) MX[B]
	[12] -1	0	0xf9ffb000 - 0xf9ffbfff (0x1000) MX[B]
	[13] -1	0	0xf9ffc000 - 0xf9ffcfff (0x1000) MX[B]
	[14] -1	0	0xf9ffd000 - 0xf9ffdfff (0x1000) MX[B]
	[15] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[16] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[17] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[18] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B](B)
	[19] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[20] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[21] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[27] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[29] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[30] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[31] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[32] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[33] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[34] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[35] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[36] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[41] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[42] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[43] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[44] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[45] -1	0	0x00007000 - 0x00007003 (0x4) IX[B]
	[46] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[47] -1	0	0x00009800 - 0x0000987f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[5] -1	0	0xf8ffe000 - 0xf8ffefff (0x1000) MX[B]
	[6] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[7] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[8] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[9] -1	0	0xf9ff4000 - 0xf9ff7fff (0x4000) MX[B]
	[10] -1	0	0xf9fff000 - 0xf9fff0ff (0x100) MX[B]
	[11] -1	0	0xf9ffa000 - 0xf9ffafff (0x1000) MX[B]
	[12] -1	0	0xf9ffb000 - 0xf9ffbfff (0x1000) MX[B]
	[13] -1	0	0xf9ffc000 - 0xf9ffcfff (0x1000) MX[B]
	[14] -1	0	0xf9ffd000 - 0xf9ffdfff (0x1000) MX[B]
	[15] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[16] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[17] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[18] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B](B)
	[19] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[20] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[21] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[22] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[23] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[24] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[25] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[26] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[27] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[32] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[33] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[34] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[35] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[36] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[37] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[38] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[39] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[43] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[44] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[45] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[46] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[47] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[48] -1	0	0x00007000 - 0x00007003 (0x4) IX[B]
	[49] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[50] -1	0	0x00009800 - 0x0000987f (0x80) IX[B](B)
	[51] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[52] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(II) NV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0xb6aad000
(--) NV(0): Total video RAM: 256.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 255.0 MB
(II) NV(0): Linear framebuffer mapped at 0xa6bad000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(--) NV(0): Connector map:
(--) NV(0):   Bus 0 -> DAC1
(--) NV(0):   Bus 0 -> SOR0
(--) NV(0):   Bus 1 -> DAC0
(II) NV(0): I2C bus "I2C0" initialized.
(II) NV(0): Output VGA1 using monitor section Generic Monitor
(II) NV(0): Output DVI0 has no monitor section
(II) NV(0): I2C bus "I2C1" initialized.
(II) NV(0): Output VGA0 has no monitor section
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C0:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): Output VGA1 disconnected
(II) NV(0): EDID for output VGA1
(II) NV(0): Output DVI0 disconnected
(II) NV(0): EDID for output DVI0
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0): I2C device "I2C1:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "I2C1:ddc2" removed.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: SPT  Model: 1734  Serial#: 263
(II) NV(0): Year: 2004  Week: 14
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #3: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Ranges: V min: 50  V max: 75 Hz, H min: 24  H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Monitor name: Sceptre
(II) NV(0): Monitor name: X7S-NAGA II
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff004e14341707010000
(II) NV(0): 	0e0e01036f221b78ea5a65a35a479a24
(II) NV(0): 	115054bfef8081808140714f61460101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300520e1100001e000000fd00324b18
(II) NV(0): 	500e000a202020202020000000fc0053
(II) NV(0): 	636570747265200a20202020000000fc
(II) NV(0): 	005837532d4e4147412049490a20002b
(--) NV(0): Trying load detection on VGA0 ... found one!
(II) NV(0): EDID for output VGA0
(II) NV(0): Manufacturer: SPT  Model: 1734  Serial#: 263
(II) NV(0): Year: 2004  Week: 14
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate  Composite  SyncOnGreenSerration on. V.Sync Pulse req. if CompSync or SyncOnGreen
(II) NV(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.638 redY: 0.353   greenX: 0.279 greenY: 0.604
(II) NV(0): blueX: 0.142 blueY: 0.068   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@67Hz
(II) NV(0): 640x480@72Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@72Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@70Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #3: hsize: 1024  vsize 768  refresh: 66  vid: 18017
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) NV(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) NV(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) NV(0): Ranges: V min: 50  V max: 75 Hz, H min: 24  H max: 80 kHz, PixClock max 140 MHz
(II) NV(0): Monitor name: Sceptre
(II) NV(0): Monitor name: X7S-NAGA II
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff004e14341707010000
(II) NV(0): 	0e0e01036f221b78ea5a65a35a479a24
(II) NV(0): 	115054bfef8081808140714f61460101
(II) NV(0): 	010101010101302a009851002a403070
(II) NV(0): 	1300520e1100001e000000fd00324b18
(II) NV(0): 	500e000a202020202020000000fc0053
(II) NV(0): 	636570747265200a20202020000000fc
(II) NV(0): 	005837532d4e4147412049490a20002b
(II) NV(0): Output VGA0 connected
(II) NV(0): EDID vendor "SPT", prod id 5940
(II) NV(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Printing probed modes for output VGA0
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) NV(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NV(0): Modeline "1024x768"x65.7   70.75  1024 1080 1184 1344  768 771 775 801 -hsync +vsync (52.6 kHz)
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Output VGA1 disconnected
(II) NV(0): Output DVI0 disconnected
(II) NV(0): Output VGA0 connected
(II) NV(0): Output VGA0 using initial mode 1280x1024
(--) NV(0): Virtual size is 1280x1280 (pitch 1280)
(**) NV(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) NV(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
(**) NV(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
(II) NV(0): Modeline "1280x960"  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync
(**) NV(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0):  Driver mode "1152x864": 104.0 MHz (scaled from 0.0 MHz), 67.7 kHz, 74.8 Hz
(II) NV(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync
(**) NV(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "1024x768": 70.8 MHz (scaled from 0.0 MHz), 52.6 kHz, 65.7 Hz
(II) NV(0): Modeline "1024x768"   70.75  1024 1080 1184 1344  768 771 775 801 -hsync +vsync
(**) NV(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) NV(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(**) NV(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) NV(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) NV(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) NV(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
(II) NV(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(**) NV(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) NV(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(==) NV(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[8] -1	0	0xf8ffe000 - 0xf8ffefff (0x1000) MX[B]
	[9] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[10] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[11] -1	0	0xfe8ffc00 - 0xfe8fffff (0x400) MX[B]
	[12] -1	0	0xf9ff4000 - 0xf9ff7fff (0x4000) MX[B]
	[13] -1	0	0xf9fff000 - 0xf9fff0ff (0x100) MX[B]
	[14] -1	0	0xf9ffa000 - 0xf9ffafff (0x1000) MX[B]
	[15] -1	0	0xf9ffb000 - 0xf9ffbfff (0x1000) MX[B]
	[16] -1	0	0xf9ffc000 - 0xf9ffcfff (0x1000) MX[B]
	[17] -1	0	0xf9ffd000 - 0xf9ffdfff (0x1000) MX[B]
	[18] -1	0	0xf9ffe000 - 0xf9ffefff (0x1000) MX[B]
	[19] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[20] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[21] -1	0	0xf8fff000 - 0xf8ffffff (0x1000) MX[B](B)
	[22] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[23] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[24] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[25] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[26] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[27] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[28] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[29] 0	0	0x00009800 - 0x0000987f (0x80) IX[B]
	[30] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[31] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[32] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d803 (0x4) IX[B]
	[34] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[35] -1	0	0x0000e400 - 0x0000e403 (0x4) IX[B]
	[36] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[38] -1	0	0x0000a400 - 0x0000a40f (0x10) IX[B]
	[39] -1	0	0x0000a800 - 0x0000a803 (0x4) IX[B]
	[40] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[41] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[42] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[43] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[44] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[45] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[46] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[47] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[48] -1	0	0x00000b00 - 0x00000b0f (0x10) IX[B]
	[49] -1	0	0x00004000 - 0x0000400f (0x10) IX[B]
	[50] -1	0	0x00005000 - 0x00005003 (0x4) IX[B]
	[51] -1	0	0x00006000 - 0x00006007 (0x8) IX[B]
	[52] -1	0	0x00007000 - 0x00007003 (0x4) IX[B]
	[53] -1	0	0x00008000 - 0x00008007 (0x8) IX[B]
	[54] -1	0	0x00009800 - 0x0000987f (0x80) IX[B](B)
	[55] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[56] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(--) NV(0): 153.75 MB available for offscreen pixmaps
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(II) NV(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) NV(0): Setting screen physical size to 338 x 270
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
SetClientVersion: 0 9

---

### Post by any.linux12 on 2009-06-02
hey man. I had the same problem you have. I don't know exactly how to help you but can you tell me which graphic card you have?

---

### Post by Bender2k14 on 2009-06-02
> **any.linux12 said:**
> ...can you tell me which graphic card you have?

Post the output of
```
lspci
```
...your graphics card will be in there.

---

### Post by Bender2k14 on 2009-06-02
(I don't think this is it, but...) do you have all the sources enabled in System -> Administration -> Software Sources -> Ubuntu Software.  Are main, universe, restricted, and multiverse all checked?

---

### Post by SkankinRatFink on 2009-06-02
> **Bender2k14 said:**
> (I don't think this is it, but...) do you have all the sources enabled in System -> Administration -> Software Sources -> Ubuntu Software.  Are main, universe, restricted, and multiverse all checked?
I don't think I can check that, I have no desktop at all. Just command line. I think they should all be checked-- I know I've installed restricted packages like media codecs. Can I check that from the command line?

> **any.linux12 said:**
> hey man. I had the same problem you have. I don't know exactly how to help you but can you tell me which graphic card you have?

It's an XFX nVidia GeForce 8400 GS.

---

### Post by SkankinRatFink on 2009-06-05
Bump ....

---

### Post by Bender2k14 on 2009-06-05
> **SkankinRatFink said:**
> I don't think I can check that, I have no desktop at all. Just command line. I think they should all be checked-- I know I've installed restricted packages like media codecs. Can I check that from the command line?

Yea, forgot that no graphics is the problem that we are troubleshooting...

Post the contents of /etc/apt/sources.list.

---

### Post by SkankinRatFink on 2009-06-10
/etc/apt/sources.list:

> # 
# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main multiverse restricted universe

# deb cdrom:[Ubuntu-Studio 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse

---

### Post by SkankinRatFink on 2009-06-15
Does that help anyone? =/

---

