---
title: "data recovery from unmountable NTFS partition"
date: 2009-02-13
forum: General Help
---

### Post by djIMP on 2009-02-13
Hi, I'm trying to recover data from my mother-in-law's laptop hard drive. Her bother thought he could make her computer run better - the result was Loading PBR2...failed. I don't know what he did but here's the situation.

with the drive in the Dell laptop: Loading PBR2...failed
with the drive attached to my laptop:
# fdisk -l

 Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           6       48163+  de  Dell Utility
/dev/sdc2   *           7       11683    93795502+   7  HPFS/NTFS
/dev/sdc3           11684       12161     3839535   db  CP/M / CTOS / ...

# mount -t ntfs-3g /dev/sdc1 /media/recovery/
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

and 

TestDisk 6.10, Data Recovery Utility, July 2008
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdb - 100 GB / 93 GiB - CHS 12161 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P Dell Utility             0   1  1     5 254 63      96327
Invalid NTFS boot
 2 * HPFS - NTFS              6   0  1 11682 254 63  187591005
 2 * HPFS - NTFS              6   0  1 11682 254 63  187591005
 3 P CP/M                 11683   0  1 12160 254 63    7679070

Also, when I ran ddrescue to copy the disk to a usb drive, after 10h only 2GB was copied, dd overnight also only copied 2GB. 

I would really appreciate some help with this. I'm not sure how to proceed with recovery since I can't mount the NTFS partition on the disk or my ddrescue copy of the partition.

thanks in advance, help me help the M-I-L, it can't make her more evil.
Mike

---

### Post by caljohnsmith on 2009-02-13
Have you tried using the "Rebuild BS" (rebuild boot sector) option in testdisk yet? If not, you can do it under the "Advanced" menu: select the Windows sda2 partition, choose "Boot", then choose "Rebuild BS"; if testdisk gives you a warning that the "Extrapolated boot sector and current boot sector are different", then choose "Write". Also, if testdisk gives you the option to "Repair MFT" (repair Master File Table) on the "Boot" screen, you could do that too. Then try mounting the partition again, and let me know how that goes, or if you can't get that far with testdisk.

---

### Post by prshah on 2009-02-13
> **djIMP said:**
> 
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           6       48163+  de  Dell Utility
/dev/sdc2   *           7       11683    93795502+   7  HPFS/NTFS
/dev/sdc3           11684       12161     3839535   db  CP/M / CTOS / ...

# mount -t ntfs-3g /dev/sdc1 /media/recovery/
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.


Have you tried mounting sdc2 (that's where the NTFS partition seems to exist)? Also, if you've not shut down correctly, you will need to force mount:

```
sudo mkdir /media/hdd
sudo chown root:plugdev /media/hdd
sudo mount -t ntfs /dev/sdc2 /media/hdd -o force,rw,defaults

```

sdc1 is not an NTFS partition and hence the error... maybe?

---

### Post by bodhi.zazen on 2009-02-13
If all else fails you can try photorec.

It is in the repos as part of the testdisk package.

How to use : [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by djIMP on 2009-02-13
caljohnsmith, no, I haven't tried that yet. I tried writing new MBR code to the partition (from the main menu of testdisk). Right now I'm making a new copy with ddrescue. Do I have to let ddrescue finish or can I try this with the partially copied partition. I don't understand why dd and ddrescue are only copying 2GB when the partition is 93GB. Anyway, I stop the ddrescue and try your suggestion, I can always restart ddrescue. 

thanks, I'll post the results.
Mike

---

### Post by djIMP on 2009-02-13
prshah, sdc1 is the copy of the partition on my usb drive. I did try the force option and got the same result. thanks for the suggestion.

Mike

---

### Post by djIMP on 2009-02-13
Oh, I was also mixing output after various plugging and unplugging of drives so the stuff I posted makes it confusing because of different drives at /dev/sdc or dev/sdb. Sorry.

---

### Post by djIMP on 2009-02-13
caljohnsmith, 

I tried your suggestions on the partially copied (ddrescue) partition. Here's what happened:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           6       48163+  de  Dell Utility
/dev/sdc2   *           7       11683    93795502+   7  HPFS/NTFS
/dev/sdc3           11684       12161     3839535   db  CP/M / CTOS / ...


testdisk summary
Advanced - Boot -
boot sector 
status: bad
backup boot sector 
status: ok

Rebuild BS - yes
boot sectors identical
Write - yes
Quit

#mount -t ntfs-3g /dev/sdb1 /media/recovery/ -o force
Record 0 has no FILE magic (0x2b0030f)
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

testdisk - advanced
Repair MFT - yes
Fixed MFT

#mount -t ntfs-3g /dev/sdb1 /media/recovery/ -o force
Record 6 has no FILE magic (0xffffffff)
Failed to open inode FILE_Bitmap: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

Any suggestions (other than those from the *mount* output?

Mike

---

### Post by prshah on 2009-02-13
> **djIMP said:**
> prshah, sdc1 is the copy of the partition on my usb drive. I did try the force option and got the same result. 

> **djIMP said:**
>  different drives at /dev/sdc or dev/sdb. Sorry.

> **djIMP said:**
> 
/dev/sdc2   *           7       11683    93795502+   7  HPFS/NTFS


Any particular reason why you are futzing around with sdc(/b)[SIZE="7"]1[/SIZE] (Dell recovery partition) instead of sdc(/b)[SIZE="7"]2[/SIZE] (HPFS/NTFS partition?)

---

### Post by djIMP on 2009-02-13
Yeah, I'm copying the second partition of the problem disk to the first (and only) partition of the the usb disk (250 GB). The copy of the partition on the usb disk is the one messing with.

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1           6       48163+  de  Dell Utility
/dev/sdc2   *           7       11683    93795502+   7  HPFS/NTFS
/dev/sdc3           11684       12161     3839535   db  CP/M / CTOS / ...

Mike

---

### Post by djIMP on 2009-02-13
bodhi.zazen,

thanks, I've been looking at photorec. I'll give it a try if I can't get the partition mounted.

Mike

---

### Post by bodhi.zazen on 2009-02-13
did you read my post and/or look at photorec ?

---

### Post by caljohnsmith on 2009-02-13
Have you tried simply doing a "chkdsk" on the partition from a Windows Install CD? If you go to the "recovery console", first do:
```
map
```
That gives the drive letters for all your partitions, and then you can do:
```
chkdsk /r X:
```
But replace X with the drive letter of the NTFS partition in question. Let me know what chkdsk says if you decide to try it.

---

