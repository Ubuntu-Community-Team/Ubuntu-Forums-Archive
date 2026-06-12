---
title: "Dual-boot problem..."
date: 2008-01-13
forum: Debian
---

### Post by XtremeGamer99 on 2008-01-13
First off, I'm not using Ubuntu, but instead Debian. But I know that Ubuntu is based off of Debian, and given the active community here, I thought I'd ask here first before I branch out to less active forums. =D

I have two Hitachi 160GB drives that I was using in a RAID0 config (thus giving me ~306.8GB available for my logical volume, *MyVolume*). Earlier today I re-installed Windows XP Pro, no problem (except for the little confusion that I had to hit F6 at the beginning of the installation to install the RAID driver). By the way, the RAID Driver that comes with my motherboard is an Intel ICH9R Southbridge controller.

I also committed myself to try and install Debian, since it's been a year or so since I last installed it on my Home PC. It went through hardware detection fine until it got to the partitioning; that's when I noticed something funny. Instead of being presented with one logical volume of 306GB -- the size of the combined drives -- like I was expecting, I am instead presented with the individual drives like so:
```

SCSI1 (0,0,0) (sda) - 164.7GB ATA Hitachi HDS72161
    >  #1  primary  128.8GB  B  ntfs
              pri/log  35.8GB  FREE SPACE

SCSI2 (0,0,0) (sdb) - 164.7GB ATA Hitachi HDS72161
              pri/log  164.7GB  FREE SPACE

```

Instead of stopping there and searching online why it was showing up like that, I went ahead like nothing was wrong, eventually creating partition tables that looked like this:
```

SCSI1 (0,0,0) (sda) - 164.7GB ATA Hitachi HDS72161
    >  #1  primary  128.8GB  B  ntfs
    >  #2  primary 35.8GB fat32

SCSI2 (0,0,0) (sdb) - 164.7GB ATA Hitachi HDS72161
    >  #1  primary  50.0GB ext3
              pri/log  112.7GB  FREE SPACE
    >  #5  logical 2.0GB  F swap  swap

```

Or something along those lines. The only bootable partition, that I know of, was the first one on the first drive (the NTFS one).

Okay, so I continue with installation, and it goes as smooth as possible (except waiting for it to download an hours worth of software >.>). I get to the point where it asks if I want to install the GRUB boot loader to the Master Boot Record. I, of course, agree, and reboot.

*Grub Error 21*

I look online, but none of the solutions seem to apply to my situation (ie: they're not using RAID). So I try to use the Windows CD Restore option: fixmbr, which is supposed to fix the Master Boot Record so that I can get back into Windows. But, as always, Windows never does what it's supposed to do, so now I'm left with a black screen after the motherboard POSTs; no GRUB error, no Windows boot, no nothing.

I plan to re-install Windows tomorrow when I get the chance. I also plan to re-install Debian, but would like a few tips from here as to what went wrong, or how I can do this properly. I read somewhere that you need to download a certain package to use RAID with Linux (something like dmraid), but I have no idea as to how to do that when I'm installing. If anyone can tell me what to do to get this all working smoothly, I really appreciate it!

PS: I'm using a 32-bit Windows XP Pro, but I'm using the x64 for the Debian 4.0 installation. I also use the *expertgui* option with the Debian installations. Just incase any of that helps. Also, other PC specs are available upon request. =D

Thanks!

Edit: an interesting bit of info: I've booted into Knoppix, and it's showing two disks on the Desktop. Both are labeled as *Hard Disk [isw_ceeihadafd_MyVolume1]* (except the MyVolume1 is MyVolume2 on the second icon). I find this interesting because this shows that it's detecting the volume label set by my RAID controller... I dunno what that means or if it helps, though. The MyVolume1 is my NFTS partition, while 2 is unknown... 0_o

Any help is great!

---

### Post by Sef on 2008-01-13
Moved to Other OS Talk > Debian.  People who look here, will be much more likely to help you.

> I thought I'd ask here first before I branch out to less active forums. =D

You can get an infraction for duplicating your thread in the same or another forum.

---

### Post by XtremeGamer99 on 2008-01-13
Uh, thanks for the move, I guess.

And when I said other forums, I meant completely different forums on different websites, not that I was going to post the same thing on numurous ubuntuforums.org forums...

<_<

I'm still having trouble with this stuff, though.

---

### Post by maybeway36 on 2008-01-14
RAID0+Linux=bad idea. :(

---

### Post by XtremeGamer99 on 2008-01-14
I have no other option though. RAID0 speeds up Windows to the point where I don't want to go back. >_>

I know Linux supports it, I just don't know how...

---

### Post by XtremeGamer99 on 2008-01-14
Also, I'm downloading the testing distro, which, from my understanding, comes with dmraid in the installer.

Is there a difference in stable and testing? IE: will 'testing' screw my computer up somehow, or not have functions available?

---

### Post by p_quarles on 2008-01-14
Testing is relatively stable, and is largely what Ubuntu itself is based on. When Debian calls a release "stable," they mean it's *stable*. I run Etch on my server, and the only time it's ever been powered off is for restarts following a kernel patch. 

For normal use situations, Testing/Lenny is fine. The only risk is that the occasional package may give you the opportunity to act as a beta tester for the stable distro. ;) You should reasonably expect the same kind of desktop functionality with Lenny as you would with Etch.

---

### Post by XtremeGamer99 on 2008-01-14
The testing distro is no good. It says that there isn't a kernal on the CD, or something like that.

I'm gonna try a netinstall next. Dunno if it'll work. Unless someone can tell me how to download dmraid to a USB, then properly load it during installation...

---

### Post by p_quarles on 2008-01-14
> **XtremeGamer99 said:**
> The testing distro is no good. It says that there isn't a kernal on the CD, or something like that.

I'm gonna try a netinstall next. Dunno if it'll work. Unless someone can tell me how to download dmraid to a USB, then properly load it during installation...
No kernel on the CD? Yikes. You sure it downloaded correctly?

In any case, the net install CD is the stable version. It's relatively safe to add the testing repository to the stable distro if you do it correctly. Doing that will allow you to get the dmraid module -- if it is indeed available in Lenny -- using the package manager. 

Here's the correct way to mix distro repositories:
[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

---

### Post by polmir on 2008-01-15
[http://www.gentoo.org/doc/en/gentoo-x86-tipsntricks.xml]("http://www.gentoo.org/doc/en/gentoo-x86-tipsntricks.xml")
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_A_Mount_Point_For_The_RAID_Set]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Create_A_Mount_Point_For_The_RAID_Set")
[http://ubuntuforums.org/showthread.php?t=630644&highlight=raid]("http://ubuntuforums.org/showthread.php?t=630644&highlight=raid")
[https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")
[https://help.ubuntu.com/community/FakeRaidDebug]("https://help.ubuntu.com/community/FakeRaidDebug")
[http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0]("http://wiki.eyermonkey.com/My_Ubuntu_%287.10%29_Installation#Installation_on_RAID_0")

I hope this helps.

---

### Post by XtremeGamer99 on 2008-01-15
Awesome. Thanks for the links and info guys. I'll sift through it tonight, and report back my findings. >_>

---

### Post by XtremeGamer99 on 2008-01-15
Okay, I re-downloaded the ISO image for Debian, and it worked fine. I now have Debian installed!

BUT. No GUI is showing up. I was expecting a boot/login screen like Ubuntu has, instead I was presented with a terminal. I logged into my account, and executed startx to start the GUI (I guess; my terminal skills are very limited...).

Nothing.

It gave me a fatal I/O error, saying that no screen was found. I looked in the X server log, and I found a list of nVidia cards under "NV: drivers for NV chipsets". My video card, a GeForce 8800 GT was not among the list, although the 8800 Ultra, 8800GTS and 8800 GTX was.

It also said something along these lines:
Primary device is: PCI 01:00.0
No Screens found.

I'll edit this post later with all included logs.

So, my primary question now is: how do I get KDE working? I downloaded the KDE ISO image, and it asked me if I wanted KDE to be used as my defualt GUI (to which I said yes), so why isn't it working? Do I need to download a driver for my 8800GT?

My secondary question: This is more about eye candy than functionality, but how do I get a GUI login screen? A nice GUI boot screen (like Ubuntu), or even somehting as simple as the colorful Knoppix boot, would be also be nice to have. How can I (if I can) configure the system to do this? Or is it a distro-based feature (ie: custom kernal).

Thanks a million for the help so far, guys! =D

EDIT: X log:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Debian (xorg-server 2:1.3.0.0.dfsg-12lenny1)
Current Operating System: Linux alpha 2.6.22-3-amd64 #1 SMP Sun Nov 4 18:18:09 UTC 2007 x86_64
Build Date: 20 October 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 15 21:58:22 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7c2f60
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
(II) PCI: 00:00:0: chip 8086,29c0 card 1043,8295 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29c1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2937 card 1043,8277 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2938 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,2939 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,293c card 1043,8277 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,293e card 1043,8277 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,2940 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2948 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,294a card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2934 card 1043,8277 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2935 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2936 card 1043,8277 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,293a card 1043,8277 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 92 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2916 card 1043,8277 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1043,8277 rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2930 card 1043,8277 rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0611 card 1682,2330 rev a2 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4364 card 1043,81f8 rev 12 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1043,824f rev 03 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1043,824f rev 03 class 01,01,85 hdr 00
(II) PCI: 05:03:0: chip 11c1,5811 card 1043,8294 rev 70 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa000000 - 0xfe8fffff (0x4900000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xf8f00000 - 0xf8ffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 3 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0611) rev 162, Mem @ 0xfd000000/24, 0xd0000000/28, 0xfa000000/25, I/O @ 0xcc00/7, BIOS @ 0xfe8e0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[1] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[2] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[3] -1	0	0xf9fff400 - 0xf9fff4ff (0x100) MX[B]
	[4] -1	0	0xf9ffe800 - 0xf9ffefff (0x800) MX[B]
	[5] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[6] -1	0	0xf9ff8000 - 0xf9ffbfff (0x4000) MX[B]
	[7] -1	0	0xf9fffc00 - 0xf9ffffff (0x400) MX[B]
	[8] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[9] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[20] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[22] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[23] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[24] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[28] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[1] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[2] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[3] -1	0	0xf9fff400 - 0xf9fff4ff (0x100) MX[B]
	[4] -1	0	0xf9ffe800 - 0xf9ffefff (0x800) MX[B]
	[5] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[6] -1	0	0xf9ff8000 - 0xf9ffbfff (0x4000) MX[B]
	[7] -1	0	0xf9fffc00 - 0xf9ffffff (0x400) MX[B]
	[8] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[9] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[10] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[12] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[13] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[14] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[15] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[16] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[17] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[18] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[19] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[20] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[22] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[23] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[24] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[25] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[26] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[28] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[29] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B](B)
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
	[5] -1	0	0xfeafe000 - 0xfeafffff (0x2000) MX[B]
	[6] -1	0	0xfe9fc000 - 0xfe9fffff (0x4000) MX[B]
	[7] -1	0	0xf9fff400 - 0xf9fff4ff (0x100) MX[B]
	[8] -1	0	0xf9ffe800 - 0xf9ffefff (0x800) MX[B]
	[9] -1	0	0xf9fff800 - 0xf9fffbff (0x400) MX[B]
	[10] -1	0	0xf9ff8000 - 0xf9ffbfff (0x4000) MX[B]
	[11] -1	0	0xf9fffc00 - 0xf9ffffff (0x400) MX[B]
	[12] -1	0	0xfe8e0000 - 0xfe8fffff (0x20000) MX[B](B)
	[13] -1	0	0xfa000000 - 0xfbffffff (0x2000000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000e400 - 0x0000e40f (0x10) IX[B]
	[19] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[20] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[21] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[22] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[23] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[24] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[25] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[26] -1	0	0x0000a480 - 0x0000a483 (0x4) IX[B]
	[27] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[28] -1	0	0x0000a880 - 0x0000a883 (0x4) IX[B]
	[29] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[30] -1	0	0x0000b480 - 0x0000b49f (0x20) IX[B]
	[31] -1	0	0x0000b400 - 0x0000b41f (0x20) IX[B]
	[32] -1	0	0x0000b080 - 0x0000b09f (0x20) IX[B]
	[33] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[34] -1	0	0x0000b880 - 0x0000b89f (0x20) IX[B]
	[35] -1	0	0x0000b800 - 0x0000b81f (0x20) IX[B]
	[36] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B](B)
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
	compiled for 1.3.0, module version = 2.1.3
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
	compiled for 1.3.0, module version = 1.2.2
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
	GeForce 8600 GT, GeForce 8600M GT, Quadro NVS 320M, GeForce 8500 GT,
	GeForce 8400 GS, GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found
```

and X config:
```

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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
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
EndSection

Section "Device"
	Identifier	"nVidia Corporation NVIDIA Default Card"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NVIDIA Default Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

---

### Post by p_quarles on 2008-01-15
You shouldn't need to download any .iso images for KDE. Unfortunately, I don't know anything about nvidia GPUs (all mine are Intel), but I can tell you how to install KDE. 

Log in as root:
```
su
```Then, install the packages:
```
apt-get install kde kdm
```Now, run startx. If your graphics card is supported, KDE will now give you the graphical login screen.

EDIT: One more thing: *before* you run startx, log out of the root console by typing "exit." You don't want to run X as root.

---

### Post by XtremeGamer99 on 2008-01-15
> **p_quarles said:**
> You shouldn't need to download any .iso images for KDE. Unfortunately, I don't know anything about nvidia GPUs (all mine are Intel), but I can tell you how to install KDE. 

Log in as root:
```
su
```Then, install the packages:
```
apt-get install kde kdm
```Now, run startx. If your graphics card is supported, KDE will now give you the graphical login screen.

EDIT: One more thing: *before* you run startx, log out of the root console by typing "exit." You don't want to run X as root.

Actually, Debian's default desktop is GNOME, but they offer and ISO image of debian with substitutes it with KDE. See the second-to-last object here: [http://cdimage.debian.org/cdimage/weekly-builds/amd64/bt-cd/](http://cdimage.debian.org/cdimage/weekly-builds/amd64/bt-cd/)

I also noticed that when booting, the last line before it asks for a login is:
*Starting K Display Manager: kdm*. I would assume it already has KDE installed.

I've also updated my last post with my X log, and also the config file... =D

---

### Post by polmir on 2008-01-15
Try it in terminal

```
su - 
```

```
dpkg-reconfigure xserver-xorg
```

and selekt item video kart **nvidia**

---

### Post by XtremeGamer99 on 2008-01-17
I got it up and running by copying Knoppix's xorg.conf to my Debian. It works now!

Thanks everyone. You've all been very helpful!

---

### Post by ssaidwho on 2008-09-28
I used Envy ([http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)) to get this working correctly.

---

