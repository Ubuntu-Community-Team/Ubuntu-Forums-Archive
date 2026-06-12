---
title: "Grub fails to start Ubuntu"
date: 2008-12-09
forum: General Help
---

### Post by wadedesk on 2008-12-09
I used Wubi to install Ubuntu 8.04.1.  The installation was successful, however Grub will not start Ubuntu and hangs when I select it from the startup list.  I believe the problem may be because Windows XP is on a SCSI drive (C) but I installed Ubuntu to the primary ATA drive (D) where there is more room.  Both are NTFS partitions.  A FAT32 formated drive and DVD-RW are located on the secondary ATA controller.  Any ideas?  Thank!

---

### Post by Jammanuser on 2008-12-09
> **wadedesk said:**
> I used Wubi to install Ubuntu 8.04.1.  The installation was successful, however Grub will not start Ubuntu and hangs when I select it from the startup list.  I believe the problem may be because Windows XP is on a SCSI [COLOR="Red"]drive (C) but I installed Ubuntu to the primary ATA drive (D)[/COLOR] where there is more room.  Both are NTFS partitions.  A FAT32 formated drive and DVD-RW are located on the secondary ATA controller.  Any ideas?  Thank!

ok...i think what ur problem is! wubi is made to be installed, on **top** of ur Windows OS...on the same partition! If XP is on C and u said u tried installing Wubi to D...there be the problem! :popcorn:

What u need to do is try installing it on C...i know u said there wasn't a enough room, but maybe u can try removing programs u don't really need, and deleting anything else that comes to mind, to clear up some disk space! ;)

Once u have installed it on C, i believe ur problem will be solved!

Cheers! :D

-jammanuser

:guitar:

P.S. go [HERE]("http://www.wubi-installer.org/") for more details on how Wubi works! Cheers! :D

---

### Post by wadedesk on 2008-12-10
I figured that it was a problem with installation location.  However it seems strange since Wubi allows you to choose the installation drive location.  

Unfortunately, there is not enough free space on C-drive to install Ubuntu.  C-drive only has WinXP OS and Office XP apps installed and there is only 7-Gb free.  

Are there any files that I can manually edited that will allow Grub to find Ubuntu on D-drive?

---

### Post by zwygart on 2008-12-10
You can edit the menu file of grub.
It is located at /boot/grub/menu.lst
I never worked with wubi.
To edit type : sudo gedit /boot/grub/menu.lst
at terminal. At the end of this file you will find the menus.
It should have a line beginnig with : title Ubuntu
followed by : root (hd?,?)
change de first ? to 1 or 0. Try switching. 
To help you with grub commands look at

[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

---

### Post by wadedesk on 2008-12-10
I found three locations for the menu.lst file:

D:\ubuntu\winboot\munu.lst  (it reads as follows)

```

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

```

D:\ubuntu\disks\boot\grub\ 
(this_folder_is_empty)

D:\ubuntu\install\boot\menu.lst  (it reads as follows)  

```

#This file is modified at runtime by bootmenu.nsh

debug off
hiddenmenu 
timeout		5
default		0

title Start installer in normal mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=syncio
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in safe graphic mode (only if you have display problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt debug debug-ubiquity xforcevesa boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=syncio
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer with ACPI workarounds (only if you have ACPI problems)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=syncio acpi=off noapic nolapic
initrd /ubuntu/install/boot/initrd.gz
boot

title Start installer in verbose mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso automatic-ubiquity noprompt debug debug-ubiquity boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=syncio
initrd /ubuntu/install/boot/initrd.gz
boot

title Read-Only Demo (Live CD Desktop)
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz iso-scan/filename=/ubuntu/install/ubuntu-8.10-desktop-i386.iso quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=syncio
initrd /ubuntu/install/boot/initrd.gz
boot

```

I can find no menu.lst on either C:\, D:\ or D:\unbuntu\

None of the menu.lst have any references to hard disk drive as shown above.

---

### Post by zwygart on 2008-12-10
I think your problem is not that GRUB find's not your drive, but that Ubuntu is on NTFS.  In your menu.lst files there are always find --set-root. I don't know wath this is, but I think this search for the file then set the root what I talked you about, but automatically. The first file sends to the second. Please post what you choose in the grub list. This should be one of the lines beginning with title in your files.
Question : The second file is it D:\ubuntu\install\boot\menu.lst or D:\ubuntu\install\boot\grub\menu.lst, have you forgotten a grub?

To access ntfs from grub, you should add a file ntfs_stage1_5 to the above folder. But I don't find this file on the net. There are others called something ending with .c Your problem is very hard. You may try install grub4dos. This should solve the problem. If you find a ntfs_stage1_5, send it me.

---

### Post by wadedesk on 2008-12-11
The problem seems to be Grub or Ubuntu recognizing a combination of SCSI and ATA drives.  I've run Red Hat (& Fedora) since 1998 and Fedora 10 fails to install miserably to the primary SCSI hdd even when there is only a CD-ROM on the ATA controller.

I tried installing Ubuntu to the FAT32 drive with the same results.  Wubi was able to copy the installation files but when I attempted to run Ubuntu the first time, it was unable to find the the install files that are not on the SCSI (C:) drive.

Just to verify, I removed programs from the SCSI (C:) drive to make enough froom for Ubuntu.  I was able to install Ubuntu on the formated NTFS SCSI drive and run Ubuntu.  However, Ubuntu was not able to see the FAT32 ATA drive on the secondary controller, but was able to mount the NTFS on the primary ATA controler.

Ultimately, I corrupted Windows on the C: drive and have had to format and start all over.  I will attempt to install Ubuntu to the (C:) NTFS drive using Wubi on the 8.10 Live CD and us the OS from that location.

---

### Post by Jammanuser on 2008-12-11
> **wadedesk said:**
> 
Ultimately, I corrupted Windows on the C: drive and have had to format and start all over.  I will attempt to install Ubuntu to the (C:) NTFS drive using Wubi on the 8.10 Live CD and us the OS from that location.

hmm...maybe u should have done that from the beginning! ;) i'm glad u **almost** got it working, though! :guitar:

Jam Man

):P

---

### Post by k64 on 2008-12-11
Why Does GRUB Boot Into A File Called Installation.iso And Not The Usual Root.disk, Then, On My WUBI Installation?

---

### Post by wadedesk on 2008-12-12
When you use Wubi to install and run Ubuntu, there is a file created that emulates an EXT3 hard disk drive in your FAT32 or NTFS file system.  You can see it in the Ubuntu folder within Windows.  It appears it the same virtual technology that Vmware uses, except the the you still dual boot and run Ubuntu as a stand-alone application rather than in a virtual machine.  This allows you to easily un-install Ubuntu since there is no permanent EXT3 or swap partitions.

I have done a base re-install of Windows XP Pro and have installed Ubuntu on my C-drive using Wubi.  After installing Wine, I'm able to run a win32 PortableApps version of Thunderbird that I have on a FAT32 drive.  This allows me to now download email and use the same portable version of Thunderbird in both Windows and Ubuntu.

The problem that I have remaining -- I can mount all ATA drives on primary and secondary buses, but the C-drive (SCSI) does not show up in my 'Places' menu.

---

### Post by Swagman on 2008-12-12
Just for your info..

If you haven't specced a SCSI hard drive install or put one in yourself then it definately WONT be a SCSI hard drive.

So why does it say you have one then ?

Because it's an old IDE hack to make IDE use the superior SCSI protocols. <--- Or something very similar to that. I can't remember the exact details (thats how old the hack is).

Regarding Using C:\ for Wubi Ubuntu installation.

It makes not one Iota of difference as far as Ubuntu is concerned. In fact it's a better bet to install it (via wubi) on a different partition. If you ever have to "dirty shutdown" Windows then your wubi install on NTFS wont have the flag set if it's on a different partition.

I installed Ubuntu via wubi on my Father in Laws machine on a second sata drive he had lying empty  ( G:\ drive) and it works like a dream.

---

### Post by wadedesk on 2008-12-12
I'm using real a real Ultra-Wide SCSI drive as my C-drive.

I've now done two clean installs of Windows XP followed by a Wubi install of Ubuntu 8.10 on the same SCSI hdd ... each time after updating Ubuntu and rebooting into Windows the NTFS partition on C-drive is completely corrupted.

I do not believe that it is possible to use Wubi on a system with a (real) SCSI drive as the C-drive.

---

### Post by Jammanuser on 2008-12-12
> **Swagman said:**
> 

Regarding Using C:\ for Wubi Ubuntu installation.

[COLOR="Red"]It makes not one Iota of difference as far as Ubuntu is concerned. In fact it's a better bet to install it (via wubi) on a different partition.[/COLOR] If you ever have to "dirty shutdown" Windows then your wubi install on NTFS wont have the flag set if it's on a different partition.

I installed Ubuntu via wubi on my Father in Laws machine on a second sata drive he had lying empty  ( G:\ drive) and it works like a dream.

That is simply incorrect...Wubi was designed to install on TOP of Windows, and not on a separate partition! ;) If u need to install Ubuntu on a separate partition, u do it that way from the beginning using the Ubuntu LiveCD...or if u already installed it via Wubi, and now want a real install, simply use LVMP to migrate the Wubi install to a dedicated partition! 

I don't believe installing Ubuntu via Wubi on a separate partition will work... :lolflag:

Cheers! ):P

Jam Man

:guitar:

---

### Post by Swagman on 2008-12-12
> **wadedesk said:**
> I'm using real a real Ultra-Wide SCSI drive as my C-drive.

I've now done two clean installs of Windows XP followed by a Wubi install of Ubuntu 8.10 on the same SCSI hdd ... each time after updating Ubuntu and rebooting into Windows the NTFS partition on C-drive is completely corrupted.

I do not believe that it is possible to use Wubi on a system with a (real) SCSI drive as the C-drive.

You may well be correct. In fact.. I may have a play on my old P3 NLE system that has a **4gb** (wow) scsi 2 fast & wide drive in it along with a couple of 60gb IDE's just to see if I can get a wubi install running on it. I'll let you know how I get on.

Oh.. Why a little 4gb scsi drive ?

That little drive cost a whopping £350 when I bought it... back in the days of the Pentium 2 and Win 95. It was one of the only drives fast enough to capture video without frame drop @ 720 x 576. 

The O/s drive was a 2.1 gb ide.  It all got upgraded along the path and the 4gb scsi drive ended up as a "scratch drive" just for odds and sods.

Here's a ----->[ **VERY old pic**](http://farm2.static.flickr.com/1406/999814736_a46a7c6c5e_o.jpg) <---- of that setup. In the tower that the Ms4 is sitting on was an Amiga 060 AND the P3 NLE machine siamesed together.

It all looks like [ **THIS** ](http://farm3.static.flickr.com/2134/2166086771_2dffb2c676_b.jpg)Now.
The original Amiga is retired... Replacement AmigaONE is next to fridge with KVM on it... NLE machine is in that white desktop underneatn. Ubuntu machine to the left. (Behind daughter). Amp was  out to springclean underneath !!

@ Jammmauser

I wonder why Ubuntu is working on my Father in Laws machine on his G:\ (sata) drive ?

Could it be that the whole system **IS** a windows system and no matter where wubi sticks the install it's STILL inside the windows environment?

Open G:\ (sata) and hey looky.... there's the ubuntu **FOLDER** in the NTFS drive.

):P

Regards
[img]http://farm3.static.flickr.com/2017/1616146653_b1963ca5c4_o.gif[/img]
[**...Paul**](http://farm3.static.flickr.com/2168/1625734937_4b8eccf9dc_b.jpg) <---- Jammin as well

---

### Post by Jammanuser on 2008-12-12
> **Swagman said:**
> 
@ Jammmauser

I wonder why Ubuntu is working on my Father in Laws machine on his G:\ (sata) drive ?

[COLOR="Red"]Could it be that the whole system **IS** a windows system and no matter where wubi sticks the install it's STILL inside the windows environment?[/COLOR]

Open G:\ (sata) and hey looky.... there's the ubuntu **FOLDER** in the NTFS drive.


hmm...it sounds like u just verified what i said! :guitar: The fact that Wubi works on ur father-in-law's system, on the G drive, is due to the fact that its on TOP of the Windows OS! :lolflag: What I was simply saying before was that Wubi does NOT work on a separate partition from Windows...which in fact it doesn't! Naturally, though, Wubi **would** work on any partition that Windows is installed on...regardless of the drive letter! 

Cheers! ):P

Jam Man (the **real** one)

:guitar:

EDIT: never mind...i apologize! i just noticed where u said that the G drive was empty...if u said it works fine for u...then i guess i take that back! Cheers! :D

EDIT #2: perhaps it only works on NTFS partitions then... :)

---

