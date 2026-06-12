---
title: "help with dual boot (ubuntu/windows 7)"
date: 2009-02-16
forum: General Help
---

### Post by racgus on 2009-02-16
I recently installed a copy of Windows 7 beta on (hd0,1). (hd0,0) is the partition in which Ubuntu is installed. 

What I would like to do is have the boot menu show not only Ubuntu as an optional OS but also Windows 7 for me to choose each time my PC is powered on. 

When I installed the Windows 7 beta, the Grub bootloader had to be reinstalled. I did this via live cd. Now I have my copy of Ubuntu loading as normal, however I am unable to choose the copy of windows that was installed on the above mentioned partition.

Any help with this issue is appreciated.

The following information may help in solving my delima:
Device Drive
(hd0) /dev/sda

Bootable Drives:
Device         Boot         Start         End       ID         System
/dev/sda1                   1             974        83        Linux
/dev/sda3        *          975           9545        7        HPFS/NTFS

Should I change the device.map to reflect these two bootable drives instead of just (hd0) /dev/sda, or does (hd0) /dev/sda encompass all partitions and should therefore reveal the partition on which windows 7 was installed?


Thanks in advance.

---

### Post by cariboo on 2009-02-16
The Windows bootloader needs to be on the first partition of the first hard drive. You may be able to create a small boot partition at the start of the drive by resizing your Ubuntu partition using gparted. The only other solution is to do a complete reinstall, putting Win 7 on the first partition and  Ubuntu on the second partion.

Jim

---

### Post by racgus on 2009-02-16
Why can't the boot menu load either, regardless of order on drive? 

Can we not change the order in which grub boots and windows boots?

---

### Post by hyperdude111 on 2009-02-16
I made a guide about how to dual boot ubuntu and Win7. Wait a min i'll find the link find the link.

**Edit**
Found the link [http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by hyperdude111 on 2009-02-16
You will need the section about configuring grub as it allows you to change the bootloader.

---

### Post by caljohnsmith on 2009-02-16
> **cariboo907 said:**
> The Windows bootloader needs to be on the first partition of the first hard drive. 
I disagree; Windows just wants any primary NTFS/FAT partition on the master drive for its boot files is all--it does not have to be the first partition. Racgus, how about trying the following entry:
```
title Windows
root (hd0,2)
chainloader +1
```
Let me know if that works or not.

---

### Post by racgus on 2009-02-16
great write up Hyperdude.

I have tried the following entry in menu.lst

title windows 7 beta (Loader)
root (hd0,3)
savedefault
makeactive
chainloader +1

I get an error when trying to select windows on boot menu. I believe it was error 17 or something like that. 

I've also tried:

title windows 7 beta (Loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

I suppose I'll try (hd0,0) and (hd0,2). If these don't work I'll try the entry caljohnsmith suggested. After that, i'm out of ideas.


I'll be right back.

---

### Post by racgus on 2009-02-16
> **caljohnsmith said:**
> I disagree; Windows just wants any primary NTFS/FAT partition on the master drive for its boot files is all--it does not have to be the first partition. Racgus, how about trying the following entry:
```
title Windows
root (hd0,2)
chainloader +1
```
Let me know if that works or not.

Thanks to both Hyperdude for his superior write up and Caljohnsmith for making me realize that I'm a freakin idiot. I just realized I had the wrong partition in the entry. 

(hd0,2) is the correct entry here. I always miss the small things. ....that's what she said. 

Thanks again fellas for your help.

---

### Post by racgus on 2009-02-16
Problem solved. 

Successfully dual booting Ubuntu and Windows 7 with Grub bootloader.


Can someone label this as solved for me...can't even figure that out.

---

### Post by caljohnsmith on 2009-02-16
Glad to hear that worked OK; cheers and enjoy Ubuntu and Win 7.

---

### Post by stchman on 2009-02-16
Leave it up to M$ to do something out of the ordinary.

TO label a thread solved go to Thread Tools.

---

