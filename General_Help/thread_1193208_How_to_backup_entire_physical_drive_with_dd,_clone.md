---
title: "How to backup entire physical drive with dd, clonezilla or other tool?"
date: 2009-06-21
forum: General Help
---

### Post by Serguei_89 on 2009-06-21
Hello

I want to install Ubuntu on my new acer aspire one, but I wish to make a full and bulletproof backup of the harddrive in it.

All the tools I know and tried, like ghost or partimage, seem to claim to backup disk, but only backup partition by partition.

I want to create an image to backup and entire **physical **disk with all it's partitions, tables, boot record.

In other words I want to be able to completely messup my partition table, boot record and still be able to restore everything back.

I heard it's possible with dd or clonezilla, but in such serious task, I don't trust merely "myself with a man page". Could you provide some more step by step instructions?

*Note: I have a USB stick with Ubuntu netbook remix and no optical drive. If I need to use dd, I'll boot into that and use terminal there. I'm backing up to a large external usb drive.

---

### Post by PhrankDaChickenGeek on 2009-06-21
It can be done with partimage, sfdisk, and dd


See:

[http://www.sns.ias.edu/~jns/wp/2006/03/21/backup-restore-scripts-for-imaging-cloning-disks-using-partimage-under-linux/](http://www.sns.ias.edu/~jns/wp/2006/03/21/backup-restore-scripts-for-imaging-cloning-disks-using-partimage-under-linux/)

I'm working on a GUI to simplify the above process - It'll be posted to [http://ubuntu.online02.com/pkimage](http://ubuntu.online02.com/pkimage)

---

### Post by tgalati4 on 2009-06-21
sudo cp /dev/sda /dev/sde

Drive should be same size or bigger.  You can use gparted to claim any left over space.

sudo fdisk -l

to get drive assignments.

---

### Post by fcvsub on 2009-06-21
[http://clonezilla.org/](http://clonezilla.org/)

is the best :)

---

### Post by Arand on 2009-06-21
> **tgalati4 said:**
> sudo cp /dev/sda /dev/sde
...

Hum? Does that actually work?

Anyhow, like PDCG said, you could do this piece by piece using dd sfdisk and partimage/ntfsclone.
Or you could just dd the whole drive, that would make a huge single copy, with bad compression, but if you have the time and space for it it would be the easiest way (If you have a 160GB drive the copy might very well be ~140GB or something, even if you're only using 20GB).
Command would be something like:```
dd if=/dev/sda bs=1024 conv=notrunc | gzip -c | split --verbose -a 3 -b 600m -d - /path/to/external/hd/mountpoint/1wholedisk_copy.dd.gz.
```# First dd copies zeroes and ones raw, passes it onto gzip which provides some compression (-c option is to pass it on again), then split is used to make 600MB bits of it, for convenience, if you ever want to put them away on a CD (read: hundreds of CDs) or something ( --verbose is for telling you when it starts on a new bit [gives some "progress" indication], -a 3 means add a suffix of 3 characters at the end, -b 600m specifies split size, -d means use number suffix [000, 001, 002, etc.], and - means recieve input (in this case from gzip), I like to name the files e.g. 1disk_clone.dd.gz.000 so that one can see what was used to create them (dd-gzip-split), but the naming doesn't really matter

To restore that you'd use something like:```
cat /path/to/external/hd/mountpoint/1wholedisk_copy.dd.gz.* | gunzip -c | dd of=/dev/sda bs=1024 conv=notrunc
```# cat is used to read all files in numbering sequence, gunzip unconpresses, and dd writes.

- Arand

---

### Post by DGortze380 on 2009-06-21
> **Arand said:**
> Hum? Does that actually work?


No it doesn't.
Use dd for bit-wise, not cp.

---

### Post by aysiu on 2009-06-21
If you want the physical disk and not just partitions, I would recommend *dd*. It is powerful and works... but it is also extremely dangerous if you are not careful.

Here's a sample for how to use it. I've used it to back up both my Eee PC 701 when I had it and my HP Mini 1120nr. The 1120nr takes longer, of course, because it's 16 GB SSD instead of 4 GB SSD.

Boot up a live Ubuntu USB session. Properly determine what your drive name is (probably something like /dev/sda) and mount your external backup (probably something like /media/disk).

The command you want to issue is ```
sudo dd if=/dev/sda of=/media/disk/backupaceraspireone.img
``` The command will take a long time to execute. If you have a 4 GB drive, it could take about 30 minutes or so. If you have a 16 GB or 32 GB drive, it could take hours.

Let me break the command down for you:
*sudo* - execute the command with root privileges
*dd* - copy the drive
*if=* - input file is
*/dev/sda* - name of input file
*of=* - output file is
*/media/disk/backupaceraspireone.img* - name of output file

It's dangerous because if you type the wrong thing, you could end up erasing your entire Acer Aspire One installation or, worse yet, erasing your entire backup medium. You want to create an image of the drive as a file on the backup. Do not back up to /dev/sdb or /dev/sdc.

You also want to make sure your backup medium is either Ext3 or NTFS. FAT32 cannot hold files larger than 4 GB.

Finally, if you want to restore your drive, you just do the reverse: ```
sudo dd if=/media/disk/backupaceraspireone.img of=/dev/sda
```

---

### Post by tgalati4 on 2009-06-22
. . . or use:
sudo cp /dev/sda /dev/sde

Be sure to get your drive assignments correct.

---

### Post by Arand on 2009-06-22
> **tgalati4 said:**
> . . . or use:
sudo cp /dev/sda /dev/sde

Be sure to get your drive assignments correct.

That is meant to clone the drive onto a new drive isn't it? And not make an image of it. Also, I thought cp was too high-level for this kind of stuff?

 - Arand

---

### Post by DGortze380 on 2009-06-22
> **tgalati4 said:**
> . . . or use:
sudo cp /dev/sda /dev/sde

Be sure to get your drive assignments correct.

No. cp will NOT make a bitwise image of the drive.
dd is the correct tool.

---

### Post by tgalati4 on 2009-06-22
Well I've used cp to clone several drives.  So it works for me.

---

### Post by DGortze380 on 2009-06-22
> **tgalati4 said:**
> Well I've used cp to clone several drives.  So it works for me.

You may have used it to make a copy of a drive ... but not a bitwise image. The appropriate tool is dd.

---

### Post by dfoguelman on 2009-06-22
Sorry I lost in the discussion.
Is dd the right tool to backup using the live cd boot?

---

### Post by KeyserSoze93 on 2009-06-22
Yes, dd should do the job...

Depending on how big your hard drive is, you can either backup onto a usb stick or backup over a lan.

To backup onto a usb stick, run:

```
sudo dd if=BLAH of=/media/STICK/drive.img
```

Where BLAH is the device file of your hard drive (should be sda, but CHECK CHECK AND CHECK AGAIN), and STICK is wherever your USB stick is mounted)

To backup over a network, there are several options, the easiest of which is netcat.

Install it on another PC where you want to backup onto ```
sudo apt-get install netcat
```

It should already ship with newer ubuntu live cds, so no need to install it there.

Run: ```
nc -l -p 8888 > ~/drive.img
``` on your target PC. Don't quit, just leave that command running and boot up the PC you want to backup with the live cd.

Then, open a term on the live cd and run:
```
dd if=BLAH | nc TARGET 8888
```
Where BLAH is your source drive and TAGET is the ip or hostname of your target PC.

When this command is done (and it may take some time, depending on the size of the hard drive), you can close the netcat which is running on the target PC (CTRL-C should do it).

To verify that your image has been created correctly, run:

```
fdisk -l ~/drive.img
``` (or wherever your pointed it at), and make sure the partition table matches that of the real hard drive.

---

### Post by arielon on 2009-11-15
This is the best option I've found in case u have, like me, enough space and time.

Cheers.

> **Arand said:**
> 
Command would be something like:```
dd if=/dev/sda bs=1024 conv=notrunc | gzip -c | split --verbose -a 3 -b 600m -d - /path/to/external/hd/mountpoint/1wholedisk_copy.dd.gz.
```# First dd copies zeroes and ones raw, passes it onto gzip which provides some compression (-c option is to pass it on again), then split is 

---

### Post by ileth on 2010-03-20
Hi all,

If I want to create a copy/clone of the disk into another disk, would dd or cp be better? I would like to make a clone and not an image. 

This is not for backup purposes but to tinker with the clone and not the original disk. So I would want to make just a clone so that I can try to rescue some data from it and keep the original disk in a safe place.

The original disk is 250GB, the target disk is bigger, but I don't think this is an issue?

So, would the command line be something like

> dd if=/dev/sda of=/dev/sdb

or

> cp /dev/sda /dev/sdb

or something else...?

Thanks in advance!

---

### Post by a.walker on 2010-03-20
I have used clonezilla multiple times and have found it very useful. Basically, you download the .iso, burn it, and then use it as a live cd. It has a simple GUI and gets the job done pretty quickly. Restoring your HD image is also really simple. So overall, it is hard to mess things up with clonezilla.

---

### Post by ileth on 2010-03-20
> **a.walker said:**
> I have used clonezilla multiple times and have found it very useful. Basically, you download the .iso, burn it, and then use it as a live cd. It has a simple GUI and gets the job done pretty quickly. Restoring your HD image is also really simple. So overall, it is hard to mess things up with clonezilla.

The thing is that I tried Clonezilla, and I just couldn't get it to do what I wanted.

The problem is that it copied the files - i.e. duplicated the contents of the partitions. I wanted to make a bit-for-bit clone of the disk, because the file systems/partitions and stuff are basically corrupt. And I just couldn't do it with Clonezilla (I spent quite a while browsing through documents how to do it but with no luck). 

I suspect dd or cp is the way to go.

---

### Post by a.walker on 2010-03-20
Yeah, now that I read through the OP instead of skimming it I agree with you.

---

