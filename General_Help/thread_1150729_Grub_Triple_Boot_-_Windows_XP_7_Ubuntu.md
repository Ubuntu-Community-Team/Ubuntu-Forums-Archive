---
title: "Grub Triple Boot - Windows XP 7 Ubuntu"
date: 2009-05-06
forum: General Help
---

### Post by pepper454 on 2009-05-06
[COLOR=black][FONT=Verdana]Is there any way to have Grub directly launch these three os's?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]My setup is a single drive with [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]-hd2,0 - Windows XP[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-hd2,1 - Windows 7[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-hd2,2 - Ubuntu[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]After intalling windows 7 i re-installed grub to 2,2.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Grub will load 2,0 but not 2,1 directly, windows 7 has installed its loader to 2,0.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I can go to 2,0 to launch XP or 7.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I want to eliminate this extra bootloader so I can use grub to directly boot the three os's.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I suppose I need to fixboot C: with the xp disc to eliminate the loader on 2,0 and boot xp directly.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Would I do the same with windows 7??? fixboot c: ??[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I hope this mostly makes sense, Thanks for any tips.[/FONT][/COLOR]
 
In the mean time I will edit the grub loader and windows loader defaults and time-outs.  "Grub" to "Windows Bootloader" to "XP".  Still feels sloppy.

---

### Post by caljohnsmith on 2009-05-06
Based on what you said, I think you are absolutely right: if you want to boot all three OSes separately from Grub, you will need to start by doing a "fixboot" on the XP partition (make sure to run the "map" command first to check which is the drive letter for the XP partition, because it may not necessarily be "C"). After that, you'll need to either move Windows 7 boot files from the XP partition back to the Windows 7 partition, or you could copy over a new set of boot files from a Windows 7 DVD. I would recommend following meierfra's excellent tutorial on "[How to fix Vista/Window 7 when the boot files are missing]("http://ubuntuforums.org/showpost.php?p=5726832")", and that should help you get the Windows 7 partition fixed so you can boot it directly from Grub. Let me know how it goes or if you run into problems.

Cheers,
John

---

### Post by EvilRick on 2009-05-07
Do you have to use GRUB?

I'm currently setup on a 120GB with 30GB for XP, ~40GB for Windows 7, and ~40GB for Ubuntu.  *I used 'gparted' after the fact of having XP and Ubuntu installed, so the /dev/sda order is a bit off.  I moved Ubuntu to the end and fit 7 between XP and Ubuntu.  Doing it again I'd create the XP, 7, and Ubuntu partitions ahead of time.  So setup would be the same, but your /dev/sda? for Ubuntu would be different than mine.

/dev/sda1 Windows XP
/dev/sda2 (Extended)
/dev/sda3 Windows 7
/dev/sda5 Ubuntu
/dev/sda6 Swap

I installed XP first and then Ubuntu.  During the Ubuntu install I chose to not load GRUB to the MBR but instead to /dev/sda5.  I ran ```
dd if=/dev/sda5 of=/bootsect.lnx bs=512 count=1
``` and copied that file over to the root of my XP partition.  Edited "boot.ini" and added ```
C:\bootsect.lnx="Ubuntu"
```

I rebooted to test that I could boot into both OSes using NT's bootloader and all was well.  Installed Windows 7 and all three OSes show up in it's new bootloader.

All three work and there's only one menu to fuss with.

EDIT - I realized I hadn't booted into XP since installing Windows 7.  After doing so, I noticed I get the second XP or Ubuntu login.  :\

---

