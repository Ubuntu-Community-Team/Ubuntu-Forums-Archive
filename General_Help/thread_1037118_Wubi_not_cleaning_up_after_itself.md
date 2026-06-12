---
title: "Wubi not cleaning up after itself"
date: 2009-01-11
forum: General Help
---

### Post by Gen. Lee poor on 2009-01-11
Hi. 
I've just got a new HP pavilion laptop, and tried to get Ubuntu 8.10 up and running using Wubi. The reason for trying Wubi first is that I've had a few negative linux experiences in the last few years with hardware compatability and so I want to check that my system will "play nice" with linux before going the whole hog. 

I tried installing wubi first a couple of weeks ago inside my 64 bit vista setup. This gave me a couple of small problems with the sound (the welcome sound just kept repeating on the login screen) and the fact that I found out about hibernation not working under wubi due to the swap file etc. 

Anyways.. I decided to uninstall wubi for the time being and then found the first issue. The windows boot menu still gave me the ubuntu option after uninstalling. 
After digging around on here, I found that I could remove it using EasyBCD (but was a bit concerned that the uninstaller didn't pick it up). I checked all was cleaned up though and deleted the c:\ubuntu folder etc. 

Today, I tried to reinstall Wubi. I downloaded a new iso file, but when I rebooted and chose ubuntu, I hit the same problem highlighted [here]("http://ubuntuforums.org/showthread.php?t=853010"). It seems that ubuntu can't find the root.disk file (I get this unknown volume type error). 

From how the guy fixed the problem (reinstalling on a new partition), I get the definate feeling that the problem is related to the old installation. Something in the ubuntu setup is trying to retrieve the root.disk file from the installation from a few weeks ago. Maybe it's somewhere in the registry? 
anyone have any gems of advice? 

Many thanks in advance. 
Nigel

---

### Post by endrit10 on 2009-01-11
I wouldn't bet getting any help from these forums any time soon.

---

### Post by Gen. Lee poor on 2009-01-11
I just looked at the issue you posted actually. 
Follow the link in the post I have linked to. See if you're getting the same error (unknown volume at /host/ubuntu/disk.image). 

As for the replies, relax. It's a Sunday evening. Give it a little time, and we'll get some gurus to pop up with some advice.

---

### Post by MxM111 on 2009-01-12
I have a qustion about hibernation not working. Does it stop working in Vista or in Ubuntu?

---

### Post by Gen. Lee poor on 2009-01-12
As far as I've read, the problem with hibernation in wubi is because Windows (XP and Vista) by default uses a swap file rather than a seperate partition for swap. 
When you put ubuntu into hibernation in Wubi, it can't access the swap file. You can get it working by creating a seperate partition in Windows for swap, but I guess this would kind of defeat the object of Wubis "no partitioning" offering.

---

### Post by brandon88tube on 2009-01-12
I'm curious, do you have a boot.ini file on your c drive (might be different letter depending on your machine)?

---

### Post by Gen. Lee poor on 2009-01-12
I don't have a boot.ini file, but interestingly, when I explore the c:\ drive, I can see a wubildr.mbr file, and another file just called wubildr. Which haven't been removed with the latest uninstall

Maybe if I try deleting these files? Anyone know if that is likely to stop Windows booting?

(Edit). Scratch that.. I just noticed that I hadn't actually uninstalled it from last night. When I removed ubuntu and deleted the boot manager entry, the files are gone.

---

### Post by brandon88tube on 2009-01-12
Is everything working for you now?

---

### Post by endrit10 on 2009-01-12
Vista does not use Boot.ini thats XP

---

### Post by brandon88tube on 2009-01-12
> **endrit10 said:**
> Vista does not use Boot.ini thats XP

Yeah, I was asking because I wasn't sure.

---

### Post by Gen. Lee poor on 2009-01-14
> **brandon88tube said:**
> Is everything working for you now?

Nope. 
I actually found out some more info too. 
On the PC I just got, there was a 10GB d:\ drive with a recovery image on it. I actually burned this image to dvds and formatted the D:\ drive, then installed wubi onto d: (as the original solution had done). This gave me the same problem. 

So from this, I guess the problem must be that "in this case", it's not possible to reinstall wubi. The problem seems therefore to be either a 64 bit Vista problem, or something specific on the HP pavilion laptop. 
It's interesting that everytime I uninstall it, it never removes the windows boot menu entry for ubuntu. There's obviously something else that never gets removed too (the pointer that tells wubi where the root.disk is), but I have no idea where it is.

---

### Post by brandon88tube on 2009-01-14
I'm not exactly sure with Vista as I've only used it a few times. In XP when you uninstall if there are files still left over delete them. If you have these files on your computer still, delete them and try again. wubildr, wubildr.mbr, the Ubuntu folder and for XP edit your boot.ini to this ```
[boot loader]

timeout=15

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /fastdetect
``` Note: the name of the operating system would be Windows XP Professional, if you had XP Pro etc... For Vista, you will have to use the Bcdedit.exe to edit the boot.

---

### Post by synapse13 on 2009-01-29
I'm running Vista 64 bit on an HP system, and after uninstall I had not regained my lost hard drive space and Ubuntu still appeared on the boot loader screen.

What I did to get back to square one: Manually delete the Ubuntu folder on your C drive, then go download EasyBCD (free download) to modify bcdedit.exe for you (this is the boot loader program in Vista).  EasyBCD does it way easier, through graphical means.  Remove the Ubuntu listing and you'll be back to where you began.  EasyBCD link:
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

