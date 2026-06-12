---
title: "How do you find the /dev/hd??/ designation of a drive?"
date: 2005-11-12
forum: Desktop Environments
---

### Post by ivanjs on 2005-11-12
I understand how to mount a fat32 partition thanks to this:

[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

but how do I find out the drive designation for a separate fat32 hard drive? I tried

sudo fdisk -l

but my fat32 drive doesn't show up in that list, although it mounts fine in Windows (it's 200 gig drive, but windows only saw 120+/- gig when I partitioned it, so I have to live with 80 lost gigs I spose). 

So my problem is, I can't use 

sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

until I know what my drive should be (instead of the /dev/hda1 shown.

I've went hda1 thru hda6 and none of that works, tried hdb1, hdc1, etc.
Thanks.
J.

---

### Post by chele on 2005-11-12
Go to System > Adminstration > Disks, then select the Hard Disk. The information should appear on the Partitions tab.

---

### Post by chele on 2005-11-12
Just a quick question. When you say it is a seperate hard drive, do you mean it is connected via USB or Firewire? Or?

---

### Post by ivanjs on 2005-11-12
[QUOTE=chele]Just a quick question. When you say it is a seperate hard drive, do you mean it is connected via USB or Firewire? Or?[/QUOTE]

It's actually a separate drive coming off my 3rd ide slot (got 3 total) as slave to a DVD burner, which, oddly enough, doesn't show up either, or is that something I have to mount manually also?

Thanks.
John

---

### Post by ivanjs on 2005-11-12
[QUOTE=chele]Go to System > Adminstration > Disks, then select the Hard Disk. The information should appear on the Partitions tab.[/QUOTE]

Thanks, I looked there first, actually, and it's not there, just my main drive that windows and ubuntu come off of, and my CD burner.

J.

---

### Post by astoltz on 2005-11-12
The third IDE slot will make /dev/hde and /dev/hdf (two per slot).  Try ```
ls /dev/hd*
``` and see whats there. That said, having three IDE slots seems a bit unusual, do the drives show up when booted into Winows?

---

### Post by ivanjs on 2005-11-12
[QUOTE=astoltz]The third IDE slot will make /dev/hde and /dev/hdf (two per slot).  Try ```
ls /dev/hd*
``` and see whats there. That said, having three IDE slots seems a bit unusual, do the drives show up when booted into Winows?[/QUOTE]

Yeah, they all show up in windows (4 hard drives and 2 optical drives). But in Ubuntu, only the cd rom and main bootable drive show up. Sad, really.

The drive I'm trying to get to show up in Ubuntu is definitely a FAT32 formatted drive.

Any other suggestions?
John

---

