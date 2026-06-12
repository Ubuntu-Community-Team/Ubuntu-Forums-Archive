---
title: "GRUB/Windows Problem"
date: 2006-09-10
forum: Desktop Environments
---

### Post by antisho on 2006-09-10
I am having trouble dualbooting with Ubuntu and Windows. Windows is on /dev/sda5 (NTFS), which could be a problem. Anyway, here is the relevant menu.lst entry.

```
title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault
makeactive
chainloader    +1
```

When I try to boot into Windows,

```
Booting 'Microsoft Windows XP'

root (hd0,4)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive

Error 12: Invalid device requested

Press any key to continue...
```

Yes, I have tried rootnoverify, and I have tried mapping (hd0,4) to (hd0,0). Neither works. I have also tried reinstalling GRUB: from within Ubuntu, not from the CD.

fdisk:
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7034    56492572+   f  W95 Ext'd (LBA)
/dev/sda2   *        7035        7296     2104515   82  Linux swap / Solaris
/dev/sda5               2        2351    18876343+   7  HPFS/NTFS
/dev/sda6            2352        4701    18876343+   b  W95 FAT32
/dev/sda7            4702        7034    18739791   83  Linux
```

fstab:
```
proc            /proc           proc    defaults        0       0
/dev/sda7       /               ext2    defaults,errors=remount-ro 0       1
/dev/sda2       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda6   	(folder name removed)	vfat	gid=1000,umask=0003,utf8,auto	0	0
/dev/sda5   	(folder name removed)	ntfs	gid=1000,umask=0003,utf8,auto	0	0
```

boot.ini, just in case (from the Windows partition; I can't write to it because it's NTFS)
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn


```

Someone, please help. :(

---

### Post by xyz on 2006-09-11
Hi-
GRUB Errors defined here [http://www.gentoo.org/doc/en/grub-error-guide.xml](http://www.gentoo.org/doc/en/grub-error-guide.xml)

as advised by Sef and other members here:
[http://www.ubuntuforums.org/showthread.php?t=114735](http://www.ubuntuforums.org/showthread.php?t=114735)

> 12 : Invalid device requested.

This error is returned if the device strings syntax is correct but other than that, an error occurred that isn't defined by any other error.

Solution

When you installed grub in your boot record using the interactive commands, did you execute the two lines below in the grub prompt?

Code Listing 3.2: Interactive installation commands

grub> root (hd0,0)
grub> setup (hd0)

(hd0,0) must be replaced with your boot partition and (hd0) with the HDD you have chosen. Remember that (hd0) will install the bootloader in the Master Boot Record of the first hard disk, the primary master.

4. 

The second link above is quite interesting but it's a long haul.
Good luck.

---

### Post by anaconda on 2006-09-11
> **antisho said:**
> 
fdisk:
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7034    56492572+   f  W95 Ext'd (LBA)
/dev/sda2   *        7035        7296     2104515   82  Linux swap / Solaris
/dev/sda5               2        2351    18876343+   7  HPFS/NTFS
/dev/sda6            2352        4701    18876343+   b  W95 FAT32
/dev/sda7            4702        7034    18739791   83  Linux
```



Hmm.. Your partition table looks strange. How did you partition your disk.

Usually extended partition is partition number 4, and all logical partitions in the extended partition come after that. eg. 5, 6, 7 etc..

so Your partition table should look something like this:
sda1 swap 7035-7296
sda2 -
sda3 -
sda4 extended   2-7034
 sda5 ntfs      2-2351
 sda6 W95 fat32 2352-4701
 sda7 linux     4702-7034

I know that even some weird partition-tables do work, and I dont know if this is your problem, but it looks strange..

---

### Post by anaconda on 2006-09-11
Ups..
Ignore my previous post. 
Actually it doesn't look that strange. Just a bit different than What I usually have..
Should be ok.

Your problem might have something to do with windows being in logical partition instead of a primary partition.

What wersion of windows do you have?

---

### Post by antisho on 2006-09-11
I looked at the grub error guide. I've done the root and setup commands from the grub prompt, with no change if I do it on the Linux partition, and an Error 17 if I do it on the Windows partition. I may try the reinstall-from-CD thing later.

> **anaconda said:**
> Ups..
Ignore my previous post. 
Actually it doesn't look that strange. Just a bit different than What I usually have..
Should be ok.

Your problem might have something to do with windows being in logical partition instead of a primary partition.

What wersion of windows do you have?
I have XP. Yes, I suspect that might be the problem. Moving it out of the extended partition, though, would require a lot of messing with partitions that I don't really want to do.

---

### Post by jerry_c on 2006-09-11
> 
fdisk:
```
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        7034    56492572+   f  W95 Ext'd (LBA)
/dev/sda2   *        7035        7296     2104515   82  Linux swap / Solaris
/dev/sda5               2        2351    18876343+   7  HPFS/NTFS
/dev/sda6            2352        4701    18876343+   b  W95 FAT32
/dev/sda7            4702        7034    18739791   83  Linux
```


It looks like your system thinks that sda2 is your boot partion. You may be having problems because windows is in an extended partition. There's an established thread on this subject that you might want to post to at: 
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")  Catlett really knows grub problems. 

Usually, you're better off posting to an established related thread than hoping for people to find your new one. If the people subscribing to the established threads can't help you, which is rare, they usually can point you somewhere with what you need.

Good luck.

---

### Post by catlett on 2006-09-11
Has windows always been on that partition? Did you move it when installing linux or did you make partitions in front of windows?
There are a couiple of things just off the top of my head.
First, your boot.ini has windows on (hd0,0) in grub terminology or /dev/hda1 in linux but it's true partition is (hd0,4)
The partition does not have a boot flag on it. It may not be booting without the boot flag.
Also I do not know a whole lot about window's partitions etc but you have a fat32 primary extended partition with an ntfs logical partition inside of it with windows. You may know windows better than me but if I had to guess, I would say the issue is trying to boot windows from an ntfs logical partition inside of a fat32 primary extended. Did this setup work before grub?
I'm going to have to look up windows and ectended partitions. It use to be a no-no but it was suposed to have changed but I need to find out for sure before saying anything else.


P.S. Start by putting a boot flag on window's partition. Open a terminal and enter  ```
sudo cfdisk /dev/sda5
```press ```
b
```to make it bootable. Then use the arrow keys to navigate the menu and exit. Then try to boot. That is the first attempt. Post any errors.

---

### Post by antisho on 2006-09-11
> **catlett said:**
> Has windows always been on that partition? Did you move it when installing linux or did you make partitions in front of windows?
There are a couiple of things just off the top of my head.
First, your boot.ini has windows on (hd0,0) in grub terminology or /dev/hda1 in linux but it's true partition is (hd0,4)
The partition does not have a boot flag on it. It may not be booting without the boot flag.
Also I do not know a whole lot about window's partitions etc but you have a fat32 primary extended partition with an ntfs logical partition inside of it with windows. You may know windows better than me but if I had to guess, I would say the issue is trying to boot windows from an ntfs logical partition inside of a fat32 primary extended. Did this setup work before grub?
I'm going to have to look up windows and ectended partitions. It use to be a no-no but it was suposed to have changed but I need to find out for sure before saying anything else.
No, it hasn't. Before I installed Ubuntu it was on the first partition and wasn't logical. But I didn't make it logical; I don't know exactly how it ended up that way on a FAT extended.
About the boot.ini, I know, but I don't know how I can change it, because the partition is NTFS. I'd probably need to boot from either a CD or USB drive with NTFS write access, unless I decided to reinstall Windows, then I'd have to deal with it messing up GRUB.
I'm pretty sure I don't know more about Windows and partitions than I do. I never had this setup before GRUB, as I said, and I don't know how it got this way.

cfdisk doesn't work. It spits out
```
FATAL ERROR: Bad primary partition 0: Partition begins after end-of-disk
Press any key to exit cfdisk
```

---

### Post by catlett on 2006-09-11
Is windows mounted when your in ubuntu? Can you open up the partition and see you files?

---

### Post by antisho on 2006-09-11
> **catlett said:**
> Is windows mounted when your in ubuntu? Can you open up the partition and see you files?
Yes.

---

### Post by catlett on 2006-09-11
Good. I was afraid you lost your windows partition or it got corrupted because there is something wrong with the partition. Grub is giving an error and now cfdisk is giving anb error.
Open up gparted and see if gparted sees the partition as a heaslthy ntfs partition or if it comes up as 'unknown' or 'unformatted'.
Open gparted by going to System<Administration<Gnome Partition Editor. If it isn't installed, install it with ```
sudo apt-get install gparted
```
Also, do you have an XP installation cd? Not a Dell of Gateway etc. factory disk but a Microsoft XP install cd?

---

### Post by antisho on 2006-09-12
> **catlett said:**
> Good. I was afraid you lost your windows partition or it got corrupted because there is something wrong with the partition. Grub is giving an error and now cfdisk is giving anb error.
Open up gparted and see if gparted sees the partition as a heaslthy ntfs partition or if it comes up as 'unknown' or 'unformatted'.
Open gparted by going to System<Administration<Gnome Partition Editor. If it isn't installed, install it with ```
sudo apt-get install gparted
```
Also, do you have an XP installation cd? Not a Dell of Gateway etc. factory disk but a Microsoft XP install cd?
gparted sees a healthy NTFS partition.
I only have a "Microsoft Windows XP Professional Reinstallation CD" from Dell.

---

### Post by catlett on 2006-09-12
Alright. Your windows partition is fine. Just wanted to make sure the partition was alright.
I asked about the cd (by the way, you have a cd that will work) because I wanted to offer a way to try and boot to windows and then dual boot again.
The idea is to restore the windows bootloader. This will remove grub from the mbr and you will only be able to boot windows. Once you have windows booting normally, you could then restore grub and hopefully this time it will dual boot.

The first step is to restore the windows bootloader. The windows XP installation disks have a recovery console on them. You have to boot to the disk and enter r at the menu. This takes you to the recovery console. from there you can get a command line. Entering ```
fixmbr
``` restores the windows loader to the mbr. This details the [http://www.geocities.com/kilian0072002/recconsole2.html](http://www.geocities.com/kilian0072002/recconsole2.html) This is an overview of the recovery console [http://www.geocities.com/kilian0072002/recconsole1.html](http://www.geocities.com/kilian0072002/recconsole1.html)

Once you are back into windows and everything is working O.K. there, go to my 'how to' and restore grub. [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) You need an Ubuntu live cd to do that process. If you have the live cd installer, that will work. What that will do is rewrite your mbr, again, with grub. What I am hoping is that windows runs a chcdsk when you boot and it 'repairs' whatever is giving up this error. Then once you can boot to windows, your grub reinstall should go smoothly.
You will find out pretty quickly if you have a bigger issue. If the fixmbr doesn't work and gives an error, then you need to reinstall or (if you have valuable data on windows) erase the linux partitions and move the ntfs windows partition to the first primary partition on the drive.
This exercise is not a guarantee. It is just me 'troubleshooting'. It is what I would try if it was me. You may find better advice somewhere or have a different plan. 
Post any errors if there are errors.

---

### Post by antisho on 2006-09-13
> **catlett said:**
> Alright. Your windows partition is fine. Just wanted to make sure the partition was alright.
I asked about the cd (by the way, you have a cd that will work) because I wanted to offer a way to try and boot to windows and then dual boot again.
The idea is to restore the windows bootloader. This will remove grub from the mbr and you will only be able to boot windows. Once you have windows booting normally, you could then restore grub and hopefully this time it will dual boot.

The first step is to restore the windows bootloader. The windows XP installation disks have a recovery console on them. You have to boot to the disk and enter r at the menu. This takes you to the recovery console. from there you can get a command line. Entering ```
fixmbr
``` restores the windows loader to the mbr. This details the [http://www.geocities.com/kilian0072002/recconsole2.html](http://www.geocities.com/kilian0072002/recconsole2.html) This is an overview of the recovery console [http://www.geocities.com/kilian0072002/recconsole1.html](http://www.geocities.com/kilian0072002/recconsole1.html)

Once you are back into windows and everything is working O.K. there, go to my 'how to' and restore grub. [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) You need an Ubuntu live cd to do that process. If you have the live cd installer, that will work. What that will do is rewrite your mbr, again, with grub. What I am hoping is that windows runs a chcdsk when you boot and it 'repairs' whatever is giving up this error. Then once you can boot to windows, your grub reinstall should go smoothly.
You will find out pretty quickly if you have a bigger issue. If the fixmbr doesn't work and gives an error, then you need to reinstall or (if you have valuable data on windows) erase the linux partitions and move the ntfs windows partition to the first primary partition on the drive.
This exercise is not a guarantee. It is just me 'troubleshooting'. It is what I would try if it was me. You may find better advice somewhere or have a different plan. 
Post any errors if there are errors.
I used the CD to fix the MBR. When I rebooted, it told me it couldn't load the operating system. Then I reinstalled grub, and it's now the same situation as before.

---

### Post by catlett on 2006-09-13
I was hoping windows would 'take care of itself'. There is one last option to try. But I think you should first copy out any important data from your windows install. At least you can access from Ubuntu copy your important data to an UBuntu folder or cd. That way you have your data in case you have to reinstall windows.
The last option I can think of is to add write support for NTFS on UBuntu. Then edit your windows boot.ini. This may be your issue when booting from windows. Actually i.t may be the underlying issue from Ubuntu as well.
Right now, your windows boot.ini says 
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
```
You need to change the 1 to 5
```
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
```
To add ntfs write support (it is still slightly dangerous because noone has the code to write the driver but it has been worked on for years) follow this How TO [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

After it is installed open your boot.ini and make the change. Then try to boot with grub. If that gives an error, you can try fixing the mbr again and see if windows loader can boot with the new .ini If that doesn't work, I would have to assume it is an with the ntfs install partition being logical instead of primary.
For now, that is all I can think of.

---

### Post by adrian15 on 2006-09-20
> **antisho said:**
> I am having trouble dualbooting with Ubuntu and Windows. Windows is on /dev/sda5 (NTFS), which could be a problem. Anyway, here is the relevant menu.lst entry.

```
title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault
makeactive
chainloader    +1
```
Someone, please help. :(

Here's the right piece of code for menu.lst:

```
title        Microsoft Windows 9x & XP Professional
rootnoverify        (hd0,0)
#savedefault
makeactive
chainloader    +1
```

Even if you think that you should load Windows XP directly from hda5 you CAN NOT because the Windows XP saves its boot files inside the first windows... that it is your hda1 where win95 or win98 or whatsoever it is.

Then from the Winxp boot loader you will be able to choose between windows xp and the other windows.

And... DO NOT MODIFY your boot.ini as catlett advises you. Windows XP bootloader sees only its partitions that means that the first one is the win9x one and the second one is the windows xp... then 0 = win9x and 1 = wixp or would it be 1 = win9x and 2 = winxp... well I just do not know.

Just try.

adrian15

---

### Post by catlett on 2006-09-20
Adrian my very well be right, I do not know much about boot.ini I just noticed it wasnt't listing your ntfs partition's position correctly.
One question Adrian, the first partition does not have a windows install.
```
/dev/sda1               2        7034    56492572+   f  W95 Ext'd (LBA)
```
That is how an extended partition is labeled. So the first partition is an extended partition that is holding the logical partitions 
```
/dev/sda5               2        2351    18876343+   7  HPFS/NTFS
/dev/sda6            2352        4701    18876343+   b  W95 FAT32
/dev/sda7            4702        7034    18739791   83  Linux
```
There is only 1 other partition and it is a primary swap
```
/dev/sda2   *        7035        7296     2104515   82  Linux swap / Solaris
```
I am a bit confuse by your comment
> Windows XP bootloader sees only its partitions that means that the first one is the win9x one and the second one is the windows xpThere isn't a windows install on the first partition. It doesn't hold any data of it's own, it is just the extended partition. Or am I missing something obvious?

I just noticed something though, the swap partition has the boot flag and your windows doesn't. Try toggloing the boot flag on
```
sudo cfdisk /dev/sda5
```

---

### Post by adrian15 on 2006-09-20
> **catlett said:**
> Adrian my very well be right, I do not know much about boot.ini I just noticed it wasnt't listing your ntfs partition's position correctly.
One question Adrian, the first partition does not have a windows install.
```
/dev/sda1               2        7034    56492572+   f  W95 Ext'd (LBA)
```
That is how an extended partition is labeled. So the first partition is an extended partition that is holding the logical partitions 
There is only 1 other partition and it is a primary swap
I am a bit confuse by your comment
There isn't a windows install on the first partition. It doesn't hold any data of it's own, it is just the extended partition. Or am I missing something obvious?

You're right. I did not read carefully.
> **catlett said:**
> 
I just noticed something though, the swap partition has the boot flag and your windows doesn't. Try toggloing the boot flag on
```
sudo cfdisk /dev/sda5
```
You're not right. An extended partition cannot be activated as far as I know from normal fdisks but from an utility from lilo... but in order to make it work you need the lilo basic bootloader.

One more thing you do not need Windows XP partition to be activated in order to be bootable as it happens in earlier windows oses.

There's another error. It is ```
sudo cfdisk /dev/sda
``` not sda5. Cause cfdisk works with full hard disks.

My new conclusion with the "new" partition table is that the boot.ini (with the 1) is correct and that the menu.lst should read as this:

```

title        Microsoft Windows 9x & XP Professional
rootnoverify (hd0,4)
chainloader    +1
boot

```

No need to make active the partition because it is not a primary one... and sometimes the savedefault command gives problems so you can remove it and then try with it. Savedefault command makes that grub remember last booted os.

adrian15

---

### Post by catlett on 2006-09-20
cfdisk can toggle the boot flag on and off partitions that are bootable. You use sudo for root then enter the partition not the drive to do it.. Which in this case is /dev/sda5. 
I do not know if this is a solution or not, it is just another suggestion while trouble shooting. Trouble shooting to me is trying 'stuff'. Whether it works or not. Usually just trying something leads to something else or someone remembers something and it gets solved.
The cfdisk is just me noticing that the swap partiion has the boot flag and the ntfs,ubuntu partitions do not. Obviously swap shouldn't have a boot flag. Is this the error, maybe not but it is another thing to try.

---

### Post by adrian15 on 2006-09-21
> **catlett said:**
> cfdisk can toggle the boot flag on and off partitions that are bootable.

As far as I know a logical partition is not a bootable one.
> **catlett said:**
> 
 You use sudo for root then enter the partition not the drive to do it..
 Which in this case is /dev/sda5. 

I will have to test it at home. I have never used cfdisk this way.
> **catlett said:**
> 
I do not know if this is a solution or not, it is just another suggestion while trouble shooting. Trouble shooting to me is trying 'stuff'. Whether it works or not. Usually just trying something leads to something else or someone remembers something and it gets solved.

The problem about his configuration was that he used the root command... this implys mounting the partition... but as far as grub cannnot read ntfs... then the mount fails... so the solution is using the rootnoverify command which does not mount the partition.
> **catlett said:**
> 
The cfdisk is just me noticing that the swap partiion has the boot flag and the ntfs,ubuntu partitions do not. Obviously swap shouldn't have a boot flag. Is this the error, maybe not but it is another thing to try.

If there's no active partition, I do not know why... an error that there's no partition active shows up on your computer. However, once, you have one partition active... it does not matter at all... what the pc boots is what it is installed on the MBR.

In this case... he has installed grub so grub boots.

adrian15

---

### Post by jonas80 on 2006-09-28
I had the exact same problem, WinXP was installed on an extended partition hda5, I tried to boot from (hd0,4) in grub but it failed.

I discovered the problem though, I had a FAT32 partition as a primary partition, and it seems that WinXP had installed its bootblock on that partition.

So I configured grub to boot from my FAT32 partition (which had no OS on it), and WinXP started from my extended NTFS partition.

---

### Post by jonas80 on 2006-09-28
Check which partition has the boot flag. If one of your NTFS or FAT32-partitions has the boot flag, that's probably the one you should be booting from. Even if there is no OS on that partition.

WinXP sets the boot flag on the partition it installs its bootblock on, it doesn't have to be the partition that contains WinXP.

---

### Post by ariel on 2007-10-21
@ Catlett: just wondering if you could finally solve your problem, and if so, how :)

Very similar issue here...
TY

---

### Post by rand0m on 2007-10-30
Did you solve this problem? I'm having nearly the same exact problem.

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          24      192748+  82  Linux swap / Solaris
/dev/sda2              25        9729    77955412+   f  W95 Ext'd (LBA)
/dev/sda5              25        4104    32772568+  83  Linux
/dev/sda6   *        4105        9729    45182781    7  HPFS/NTFS
```

It worked in Feisty but I wiped that partition and put in a clean Gutsy, now windows won't boot and produces the same error 12.

---

