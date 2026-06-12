---
title: "Run-int: /sbin/int:no such file or directory"
date: 2008-12-31
forum: General Help
---

### Post by MopMonkee on 2008-12-31
*hits head against brick wall* 

Scenario:
Been using Ubuntu (8.04) since August. Had some issues in the past. Haven't been able to update in a couple months. But this never bothered my day-to-day activities so I just ignored updating. *hits head against brick wall* 

Whenever my computer decides to do disk scan from boot up as routine it would always fail. I learned that skipping it and doing a manual (sudo fsck -fv /dev/sdb1) fixed some problems and made this issue go away for a month or so.

This particular incident occurred again and I busted out the manual scan. This time I encountered this message: WARNING!!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Ignoring this I scanned again. *hits head against brick wall* 
When I went to reboot my loading bar freezes and computer sits.

Running in safe mode under both kernels at my disposal I encounter a pile of unreadable material ending with this: 
Begin: Running/scripts/init-bottom...
Done.
Run-int: /sbin/int:no such file or directory
[ 22.890184]Kernel Panic - not syncing:Attempted to kill init!


What I have attempted:
Reading through the forums I find this is a common error related to many different types of problems.

What seems to bother people most is faulty ram or HD. I have taken each piece of ram out in turn to see if this is the case and no luck. (still freezing on loading bar).

Run ubuntu from live cd and again try to do a manual fsck scan. This does not seem to help.

I try downloading and installing updates while on the live cd. I am able to download updates but run into issues installing (see error1.txt)

My Suspicions: 
I am encountering 2 problems?
An update issue which stems from a voodo curse?
As for the boot freezing I suspect there is some sort of mounting problem or linking issue to my kernel. Although I am a ultra-noob I am completely comfortable with being wrong. 

Hardware:
2 Hard-drives(IDE)
250gig - holds Ubuntu and programs
300gig - holds long term data (music, pictures ect.)
Hard Drives work separately from each other and have had no issues there.

Radion x800 graphics card
2gigs of ram 

Plea for help:
Is there anyone out there who can help me get my pc running again

---

### Post by hal8000 on 2008-12-31
Boot from the live CD then post the output of the following:

sudo fdisk -l

This will list partitions, do you know where your / partition is?

Do you know what file system you used ext3 , ext2, reiser or other when you installed Ubuntu?

/sbin/init: no such file sounds like you have missing files, or a corrupt/damamged hard drive.

---

### Post by MopMonkee on 2008-12-31
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x076adc61

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004529d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29644   238115398+  83  Linux
/dev/sdb2           29645       30401     6080602+   5  Extended
/dev/sdb5           29645       30401     6080571   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by MopMonkee on 2009-01-03
Any Ideas?

---

