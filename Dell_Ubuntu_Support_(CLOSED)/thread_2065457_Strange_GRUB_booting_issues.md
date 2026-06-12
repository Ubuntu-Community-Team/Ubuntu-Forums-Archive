---
title: "Strange GRUB booting issues"
date: 2012-10-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arandomstring on 2012-10-02
Hey, I'm currently on a Dell 17R Special Edition and I'm experiencing issues dual booting Ubuntu 12.04 and Windows 7. I have two hard drives, however one of them is a SSD used in Windows as a caching device to speed up booting (Intel Rapid Storage Technology I'm assuming?) Anyway... On my main hard drive (1 TB) I have 4 partitions (screenshot attached), which are:

[LIST]
[*]a 39.19 MB DellUtility FAT16 partition (has the diag flag)
[*]a 18.83 GB RECOVERY partition (has the boot flag)
[*]the Windows 7 partition (417 GB)
[*]and the Ubuntu partition (478 GB with a 15.83 GB swap)
[/LIST]
First off, GRUB detects windows 7 on 3/dev/sda2/ when it is actually on dev/sda3/. When I select to boot Windows it goes to the screen saying boot files were changed yadayada and to select startup repair or start normally. I've always selected start normally with the fear selecting repair would only worsen my GRUB situation. After continuing past that menu Windows attempts to boot. But fails and sends me back to a completely blank screen where Windows seemingly checks for problems (Ex. items are listed and a completion percent is beside them.)


Once this page is complete Windows boots completely fine and everything is smooth from there. Until I reboot.... GRUB doesn't even appear and Windows boots immediately. However if I shutdown and reboot GRUB is usually back (sometimes I hold left-shift although I'm not sure if that has any effect.) Once I'm into GRUB again it STILL lists Windows as on /dev/sda2/. 


Another minor problem is Gparted has a strange error saying on the real Windows partition saying the filesystem check failed. The error goes beyond the screen though so I can't view its entirety.


Anyway, I've tried all of the standard fixes (updating GRUB, using Boot-Repair from a LiveCD etc.) but nothing works. My suspicions are the DellUtility or RECOVERY partitions have something to do with it, but I don't know. I don't think I can just delete them though because they are on the start of the disk. If anyone has ANY insight as to what could be causing this I would appreciate it immensely!


Thanks for reading this all!


EDIT: Thought I'd add a screenshot of the SSD from Gparted as well

---

### Post by arandomstring on 2012-10-02
Bump. Anyone?

---

### Post by Bashing-om on 2012-10-02
madkristoff; Hi !

I'll take a stab at it ..be advised I am no longer windows savvy, but here goes what I can.

I see the sda1 as an UEFI boot partition  (12.04 has updates to cope with UEFI).

See these links in that respect and see if they help, please post back with your results.
[http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise](http://ubuntuforums.org/showthread.php?t=2059640 dual boot & UEFI advise)
[http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI](http://ubuntuforums.org/showthread.php?t=1974392 <-Dual booting UEFI)
[https://gitorious.org/tianocore_uefi_duet_builds/pages](https://gitorious.org/tianocore_uefi_duet_builds/pages)
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

### Post by oldfred on 2012-10-02
While the first partition being FAT seems like it may be UEFI, that you have an extended partition says MBR and Windows only installs to UEFI in gpt partitioning. Did in trying to install you convert from gpt to MBR?

If you want to boot Ubuntu in the SSD, you have to remove the RAID settings. That means Windows will not have the speedup from the Intel SRT.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by arandomstring on 2012-10-03
Judging from the info in your second link Bashing-om, Ubuntu is not installed in UEFI. This is what specifcally tipped me off: 

> **immerohnegott said:**
> 
You'll know if the Ubuntu installer is loading in BIOS emulation if you  get the normal purple screen with the accessibility and keyboard icons  at the bottom. In UEFI mode, it just loads a black and white GRUB menu.

 So I'm assuming I have it installed in the regular fashion as that icon appeared during install.

---

### Post by arandomstring on 2012-10-03
> **oldfred said:**
> 
If you want to boot Ubuntu in the SSD, you have to remove the RAID  settings. That means Windows will not have the speedup from the Intel  SRT.
 


I don't want to boot ubuntu from the ssd unless I have to. I installed it already to the main hard drive obviously, but I did have trouble doing so at first. (Only the ssd was listed) The solution I found was running ```
sudo apt-get remove --purge dmraid
``` after that I could see both drives and installed correctly on the 1TB.

EDIT: Hey, I just finished reading all of the links you guys posted and I think I found a solution. Stop Windows from booting off the ssd, change the BIOS so it doesn't use it and hopefully that will work. However I have no idea how to go about this... Any help?

EDITEDIT: Fixed my issues everyone! Thanks for your assistance! In the spirit of preventing [this]("http://xkcd.com/979/"), I will explain my fix. Using one of the threads you two listed I found out that installing the actual Intel Ready Start program was required. I thought I had it because of the icon on the tray in Windows, but I was wrong. I only had the "manager" (which didn't really manage anything....) after installing the real program the GRUB issues were corrected. In order to fix the problems Gparted was having I just did as it suggested, run chkdsk /f twice. I hope this will help someone in the future! SOLVED.

---

