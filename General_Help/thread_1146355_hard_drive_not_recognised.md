---
title: "hard drive not recognised?"
date: 2009-05-02
forum: General Help
---

### Post by tubunu on 2009-05-02
Please help me out here... :cry:

After upgrading to a new PC and trying to transfer the old SATA hard disk to the new PC, it is not recognized. It starts making strange noises during the booting of the system, but then it's not listed anywhere. I checked the BIOS settings and the SATA cables seem to be plugged in correctly. 

I had a 5 years worth of data (work documents!) on it and now I cannot access the drive. I don't care for the drive, just the documents. Could someone please advise what I could try to do to recover the files? 

I searched online and there's an option of connecting the drive via USB port, do you think this would work? Another option I've researched is ddrescue, but I don't know how to copy the files if the drive isn't recognised? :confused: I'm at a loss.. 

Thank you in advance for any insight.

---

### Post by logos34 on 2009-05-02
what does 

sudo fdisk -l

show?

---

### Post by tubunu on 2009-05-02
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4866    39086113+   7  HPFS/NTFS

```


The sda drive is the only one that's listed. The other one, which I can't get to boot isn't listed although it's attached with cables, etc. Every now and then I can hear it make a short sound. :(

Should I go ahead and try freezing it in the fridge? :P

---

### Post by codeseer on 2009-05-02
> **tubunu said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4866    39086113+   7  HPFS/NTFS

```


The sda drive is the only one that's listed. The other one, which I can't get to boot isn't listed although it's attached with cables, etc. Every now and then I can hear it make a short sound. :(

Should I go ahead and try freezing it in the fridge? :P

Have you tried with just it plugged in and no other drives?

---

### Post by Yellow Pasque on 2009-05-02
It makes strange noises? Does the BIOS recognize it? If the BIOS can't detect it, there's no point in trying to get the OS to recognize it.

EDIT: If the BIOS lists it, look through your dmesg output to see if there's any mention of it.

---

### Post by tubunu on 2009-05-03
> **Temüjin said:**
> If the BIOS can't detect it, there's no point in trying to get the OS to recognize it.

The BIOS lists my other 2 HDDs but not this one. Does that mean that I can say goodbye to it? Is there a way to revive the hard drive somehow? It's strange because in one PC it was working, I moved it to the other one and all of a sudden it started making noises and stopped being recognized. :confused:

I'll be grateful for any other piece of advice that I could try. Thanks!

---

### Post by tubunu on 2009-05-03
Does anyone have any positive results of plugging a failing hard drive via USB?

---

### Post by codeseer on 2009-05-03
> **tubunu said:**
> Does anyone have any positive results of plugging a failing hard drive via USB?

I've talked to a couple people that it's worked for, but I've never done it myself.

---

### Post by tubunu on 2009-05-03
I'm going to give it a try. Will post back.

---

