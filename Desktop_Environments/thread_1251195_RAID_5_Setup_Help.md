---
title: "RAID 5 Setup Help"
date: 2009-08-27
forum: Desktop Environments
---

### Post by superfly85 on 2009-08-27
I have 3 1TB disks that I cleared, 2 are Samsung F1's and 1 is a WD Green. Tried to build a raid 5 array using Nvidia fake raid in the BIOS but the kernel doesn't support/include dm-raid45. I downloaded the source for dm-raid45 but don't know how to incorporate it into the kernel (have never compiled or patched a kernel). After I disabled fake raid, Ubutnu only sees one of the drives (I'm guessing I have to wipe each individually). No luck so far with mdadm soft RAID. Would a raid card help me or be useless because of the drive mix and match? I would rather let mdadm build the array because I rather not drop $300 on a card that may not work and from what I hear Nvidia fake RAID is terrible.

Why can I not see the drives any more? (I used Gparted)
What is my best option?
How can I provide more information on the problem?

Any help or insight would be much appreciated, Thanks in advance. ~Alex

---

### Post by i.r.id10t on 2009-08-27
I'm using a no-name SATA II controller card, 3 1tb WD disks, and mdadm raid-5 ... no issues.

---

### Post by tgrimley on 2009-08-27
Device mix and match doesn't matter as long as they're all the same cylinder size.  I can't figure out if that motherboard has more than one sata controller.  sometimes there are two controllers and one may be enabled / supported by the kernel and the others are not.  Can you say?

How are you trying to detect the existence of the drives?  If gparted can't see them it's likely because ubuntu cannot (which would probably be because it cannot see the sata ports).

please provide as much info as you can.

---

### Post by superfly85 on 2009-08-27
The BIOS is detecting all three drives in question, Right now I am booting from an old 60GB IDE drive so I can freely work the problem.  The drives were being detected just fine up until I tried using the Nvidia Fake raid.  When I turned the RAID option on in the BIOS, enabled the SATA channels it would report: "Nvidia 1.7TB RAID5 Healthy"  but this array for one reason or another was invisible to Ubuntu.  One odd thing I did notice was, normally a 1TB drive is reported as 931 gigs but after setting the fake raid it was being reported as 1000.2GB (the two other two drives were still invisible, Both Samsungs I think).  My theory is that something was written across all the drives that was not undone or deleted when I disabled the Fake Raid.  From what I gather The drive that is being reported is the WD Green.  What commands should I run to show you some information regarding this problem, I've been trying to figure this out for a few weeks now without much luck and the book "A Practical Guide To Ubuntu" by Sobell doesn't provide much (although its been the best computer book I've read so far).  Should I yank out each drive and format them from an external enclosure (USB)? thanks to all. 

sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ec59d

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91499149

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6994    56179273+  83  Linux
/dev/sdb2            6995        7297     2433847+   5  Extended
/dev/sdb5            6995        7297     2433816   82  Linux swap / Solaris
superfly@SuperflyServer:~$

---

### Post by superfly85 on 2009-08-27
What should I format the drives to EXT3 or EXT4?

---

### Post by superfly85 on 2009-08-27
Sorry for all the edits but I had a 1TB external HDD hooked up that I failed to mention when I pasted the output of fdisk -l.

---

### Post by paulisdead on 2009-08-27
As to having the drives sizes being misreported, try re-enabling the fake raid, and go into the bios for the raid config and delete the array, reboot and disable the fake raid in the bios.  I've had issues when fake raid metadata has been written to the drives, and tried to use the drives individually or in a soft raid.

As to ext3 vs ext4, it's really up to you.  I've had no issues with ext4, but haven't trusted it to any of my servers and really important data, yet.  I've been running it on my htpc, desktop, and laptop, all with really different hardware, and not seen an issue.  You do get a bit better performance in general, but the huge things I noticed are the filesystem checks and deleting files are nearly instantaneous with ext4.

Ext3 might be a bit slower, but it's very solid and well supported filesystem.  If you're worried that important data could be lost, I'd probably stick with ext3.

I generally advise against mixing hardware in RAID setups, it's just bad practice, since the slowest drive can cause delays.  If you're really dead set on it, make sure the partitions on all of them are exactly the same size for mdadm, so you might have to leave a little left over on one or two of the drives.

---

### Post by superfly85 on 2009-08-27
Thanks I'll try that now, I guess I'm going with EXT3 just to be on the safe side.  Also when you mentioned the mix and match of the drives, which raid were you referring to hardware or soft or both?  I would love to have another Spinpoint so I could have the 3 Drives of the exact same make and model but I have a cash flow problem right now.  Hint: (its flowing in the wrong direction).

---

### Post by superfly85 on 2009-08-27
I enabled the Fake raid, rebooted, then deleted the array, rebooted, then disabled fake raid from the bios, rebooted. no dice :(, but I think you were on to something about the metadata, that would make a lot of sense, how would I go about deleting it?

---

### Post by superfly85 on 2009-08-27
The new output of fdisk -l :

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91499149

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6994    56179273+  83  Linux
/dev/sdb2            6995        7297     2433847+   5  Extended
/dev/sdb5            6995        7297     2433816   82  Linux swap / Solaris

---

### Post by superfly85 on 2009-08-27
OK, I just removed all the disks except for the one being detected (WD Green), I'm about to format each individually starting with this one, using gparted, correct me if I am wrong but the partition table should be msdos?

This is how I plan to do it;

Primary partition --> EXT3

set the raid flag

is this correct?

---

### Post by paulisdead on 2009-08-28
> **superfly85 said:**
> OK, I just removed all the disks except for the one being detected (WD Green), I'm about to format each individually starting with this one, using gparted, correct me if I am wrong but the partition table should be msdos?

This is how I plan to do it;

Primary partition --> EXT3

set the raid flag

is this correct?

Until you've created a md device, filesystems don't come into play at all.  You want Linux software RAID for partition type on all the drives.  Once they're all partitioned as Linux Software RAID, you can then create the md device, or array using those partitions.  Then finally, you can format the md device (probably /dev/md0) as ext3.  You're not so much RAIDing devices as you are individual partitions.

---

### Post by superfly85 on 2009-08-28
I got it !!!!!!!!!!!!!!!!!!

It was either a bad sata cable or something, after taking out every drive and formating them putting them back only 2 out 3 drives would be detected by Ubuntu.  Then I took the third drive and hooked it up to a working sata cable + port and presto.  

it labeled the drives 

/dev/sda
/dev/sdb
/dev/sbc

and it pushed my IDE drive with the OS from sdb to sdd 

Tagged them all with the raid flag and formated them to EX3


ran this command:

sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1  



Then ran this to check progress:

sudo watch cat /proc/mdstat

Right now im at 7.2% 

this is the guide Ive been using 

[http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)

---

### Post by superfly85 on 2009-08-28
Moral of the story NEVER use Nvidia Raid or any FakeRAID for that matter. 


Will update this when its done.

---

### Post by tgrimley on 2009-08-28
I missed all the action!  Glad to see you've got things dialed in now!

---

### Post by superfly85 on 2009-08-29
sudo umount /dev/md0
superfly@SuperflyServer:~$ sudo badblocks -vswp 2 /dev/md0
Checking for bad blocks in read-write mode
From block 0 to 1953524991
Testing with pattern 0xaa:  47.14% done, 20:14:33 elapsed

---

### Post by superfly85 on 2009-09-07
I can't seem to get it to stick, every reboot the device has to be rebuilt

~BTW went with ext4 for the file system 

also added this to line to fstab:

/dev/md0	/mnt/md0	ext4	defaults	1	2

And.... This for the mdadm config:

mdadm --detail --scan > /etc/mdadm/mdadm.conf

fdisk -l gives me this now:

Disk /dev/md0: 2000.4 GB, 2000409591808 bytes
2 heads, 4 sectors/track, 488381248 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

---

### Post by superfly85 on 2009-09-07
OK after the fstab and config file additions I think it works !!!

copied some test data and rebooted, and its still there!!!

but.... I don't think I have it right yet, it does not come up as a drive and gparted still sees the drives as single and unformatted, also anyone who can tell me what to make of this fdisk -l output would be a god send right now....

fdisk -l

Disk /dev/md0: 2000.4 GB, 2000409591808 bytes
255 heads, 63 sectors/track, 243202 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      121602   976762583+  8e  Linux LVM


*the results of the drives making up the array /sda /sdb and /sdc are still being reported as "doesn't contain a valid partition table"

So I just made a link to the folder /mnt/md0 and dumped the data in there, this seems kinda wrong, what is [md0p1}?????

---

