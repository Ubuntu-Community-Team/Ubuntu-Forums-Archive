---
title: "TrueCrypt Mounting Error"
date: 2009-06-09
forum: General Help
---

### Post by evropej on 2009-06-09
First, I am new here so be kind because this the first post.
Second, I searched the forums and consulted google with no luck so far.

So, here is the issue. 
I am using truecrypt 6.2.
I have an encrypted volume which I can mount in my 500 gig NTFS drive. Works just fine.
I also have an encrypted volume on a tera byte drive which I am having problems with.
Its the same type of encryption as the 500 volume and same type of file system, NTFS. This volume works fine in Windows since I am using a dual boot machine.

Here is the error message.

```
$MFTMirr does not match $MFT (record 24).
Failed to mount '/dev/mapper/truecrypt1': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```I did a fdisk dump so you can see the volume data
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ad1526f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7711a7d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xccdb290c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001    7  HPFS/NTFS
chromoton@ubuntu:~$ 

```I have read a lot of articles but no luck so far. It seems as if the 3g ntfs driver has a bug or an issue. Any help would be appreciated. 
Thanks

PS I am a linux super noobie so be very descriptive in explaining things

---

### Post by michy99 on 2009-06-09
This is just a guess on my part but it is worth trying out. If an ntfs disk is not unmounted properly in windows, it will not mount properly in linux. Boot into windows and make sure you unmount it properly with the 'safely remove hardware' or whatever it's called. If that doesn't fix it we will have to try something else.

---

### Post by evropej on 2009-06-09
Ok, I have two truecrypt volumes on my 500 GIG. Both are the same type. One I can mount, the other I get the same error. 

Both drives are accessible to normal NTFS files. I can copy and delete files just fine. The one 500 encrypted volume works just fine.

I logged into windows and mounted both and dismounted as suggested, no luck.

I think this is a force mount issue but no sure how I got around it a while back.
Oh yeah, using Ubuntu 9.04

---

### Post by michy99 on 2009-06-09
So both volumes are on the same drive. Both mount properly in windows and only one mounts in Ubuntu. Have I got it right? Is this an internal or external disk? Do you have an entry in fstab to automatically mount the disk when you boot?

Just trying to get information to see if we can figure this out:)

---

### Post by evropej on 2009-06-09
Yes, both mount correctly in windows. The volume file system is NTFS. The drive file system is NTFS. This is an internal hard drive. No I dont have any entries in the fstab to auto mount the drive.

Can you explain what is fstab?

---

### Post by michy99 on 2009-06-09
fstab is a text file located at /etc/fstab which tells ubuntu which drives to mount at bootup and how to mount them. If one truecrypt volume works fine and the other doesn't then it probably isn't an issue.

Did you try this procedure as suggested in the error message:```
In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! 
```

Also I am still confused (it happens to me a lot) because you first said that one volume was on a 500 gig drive and the other was on a 1 terabyte drive, but later you seemed to be saying they are on the same drive.

---

### Post by evropej on 2009-06-09
i will try the

chkdsk /f

---

### Post by evropej on 2009-06-09
chkdsk /f with two reboots and no dice
HaLP!!!

[-X

---

### Post by michy99 on 2009-06-09
Can you please clear up for me the question of whether the two truecrypt volumes are on the same drive or different drives?

---

### Post by evropej on 2009-06-09
i have a 500 gig with two truecrypt volumes, one which works and one that does not
i have a 1000 gig with one truecrypt volume which does not work
both drives are accessible in ubuntu, read and write

---

### Post by michy99 on 2009-06-09
Ok, so there are three truecrypt volumes in all. In Ubuntu, one works and two do not. In Windows, all three work. Do I have it right now?

The only suggestion I have is to backup all the data in Windows, delete the problem volumes, and create new volumes to see if they work any better.

Sorry, I don't have any better ideas. Maybe someone else will come along who knows more than we do about this.

---

### Post by evropej on 2009-06-09
formatting a tera byte drive is not an option. i have 800 gigs of data. backing it up, formatting and recopying is a three day ordeal.

---

### Post by michy99 on 2009-06-09
Sorry I wasn't able to help. Maybe you will have more luck in the truecrypt forum:

[http://forums.truecrypt.org/](http://forums.truecrypt.org/)

Good luck.

---

### Post by evropej on 2009-06-09
michy99,
you need a paying email account to use their forums believe it or not. i am googling myself to death. i am more confused now then when i started. i figured this out long time ago but never wrote it down. thanks for trying.

---

### Post by evropej on 2009-06-10
bump?
:D

---

### Post by evropej on 2009-06-10
bump bump
:(

---

### Post by evropej on 2010-08-05
solved the problem
you need to mount the volume in windows
then scan the encrypted volume and not the drive the file exists on
do this twice and its good to go

---

