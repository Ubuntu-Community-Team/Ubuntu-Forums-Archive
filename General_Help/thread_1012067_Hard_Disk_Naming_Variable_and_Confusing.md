---
title: "Hard Disk Naming Variable and Confusing"
date: 2008-12-15
forum: General Help
---

### Post by mattyj on 2008-12-15
Hello,

I have a machine running 8.10 64 bit with one 160GB 10k drive with the OS, and two 500 GB hard drives.  I have had trouble with the two 500GB drives being recognized.  First I have to go to PLACES--REMOVABLE MEDIA and select them every time to get them to mount.  This is not a big deal.

It used to call them disk and disk-1 mounted under /media/disk and /media/disk-1 respectively.  Now there are several more mountpoints /media/disk, /media/disk-1, /media/disk-2, and /media/disk-3.  

This is what my setup looks like despite only having two hardisks (when I open disk and disk-1 they are empty folders), whereas those used to hold the content of my two drives...

mj@mj-desktop:~$ cd /media
mj@mj-desktop:/media$ ls
cdrom  cdrom0  cdrom1  disk  disk-1  disk-2  disk-3


It seems to be adding more every time I restart.   This gets very confusing especially as I mirror one drive to the other.  Also programs with links get confused by the changing naming scheme.  This all started when I put in a USB flash drive, but now no other disks or flash drives are mounted.

Can you suggest a way to just have these hard disks mount automatically to the same place every time?  I have tried editing /etc/fstab but this resulted in no disks being mounted and ubuntu seemed to be confused.

What I would like is them being mounted in the same place with the same name every time.  I have never had this much trouble with ubuntu and disks before.



This is the current contents of my fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=64c800a3-34f8-487f-95e2-cd929ee31faf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


Thank You for your help.

---

### Post by moberry on 2008-12-15
That is the automounter at work. If you are going to use the drives at all times; you are probably best adding fstab entries for both drives.

---

### Post by mattyj on 2008-12-15
> **moberry said:**
> That is the automounter at work. If you are going to use the drives at all times; you are probably best adding fstab entries for both drives.


Thank You.  What is the best example site etc for configuring that.  I had not had trouble in the past, but something seems different now with ubuntu...

MJ

---

### Post by moberry on 2008-12-15
Quick google search gave me this:

[http://en.wikipedia.org/wiki/Fstab](http://en.wikipedia.org/wiki/Fstab)

Looked good at a glance.

---

### Post by drs305 on 2008-12-15
Here is another good link:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

If either of the extra drives are NTFS format, there is an easy method to add them to your fstab.
Install and run the NTFS Configuration Tool:
```

sudo apt-get update
sudo apt-get install ntfs-config
sudo ntfs-config

```

I would recommend using UUIDs to identify the devices in fstab. You can get the UUIDs by running:
```

sudo blkid

```

---

### Post by mattyj on 2008-12-15
Thank You.

I checked things out my mounting the disks to my desktop and it does something weird.  I make a folder called sdb1 for the drive and mount it to that point.  When I do so the folder remains but a hardrive icon also shows up which has the same contents as the folder and is a representation of the same drive and its contents.  I don't really need both and it gets confusing as it only sayes 500.1GB drive no matter which drive I am using.  

Is there a work around on this?  I am fine with just having one or the other (the actual mount point or a disk icon with a name I pick).

Both disks are ext3, pure linux workstation...

Thank You,

Matt

---

### Post by moberry on 2008-12-15
I would use tune2fs to give each drive a drive label. Gnome will then display the label instead of the highly generic "500.1gb Media"

tune2fs -L "label" /dev/sdb1

---

### Post by drs305 on 2008-12-15
> **mattyj said:**
> I don't really need both and it gets confusing as it only sayes 500.1GB drive no matter which drive I am using.  

Is there a work around on this?  I am fine with just having one or the other (the actual mount point or a disk icon with a name I pick).

Matt


I just reviewed your post and am not sure if you are talking about seeing them in nautilus or on your desktop. The following regards desktop icon displays....

You can probably hide the second icon (the actual drive) by electing not to show mounted volumes on the desktop. The disadvantage to this method is that it won't show *any* volumes, including cdroms you just inserted, etc.

To hide the volumes, you can edit the gconf-settings manually via "gconf-editor" or just run the following command. (To display them again, just change the value to 'true'):
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

P.S. I second the recommendation of tune2fs

---

### Post by mattyj on 2008-12-15
Thank You very much.  I greatly appreciate your help.  I moved the mount folders to my home directory and this is my fstab.  Everything mounts in the correct place, the only weird thing is that one 500.1 GB Media icon shows up on the desktop corresponding to sdb1, but nothing shows up for sdc1.  Being I set them up identically it is not clear to me why this is.

I would like to use the program you specified to label each so they show up with their actual identifier, not sure why the second drive doesn't show...

This is my fstab...

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=64c800a3-34f8-487f-95e2-cd929ee31faf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6c2e2e8b-8228-48d5-af9e-3ee466efd719 none            swap    sw              0       0
# /dev/sdb1
 UUID=d59347b1-8a2a-4608-ba7c-6f163d175c98 /home/mj/sdb1 ext3  exec,relatime  0  2
# /dev/sdc1
UUID=d59347b1-8a2a-4608-ba7c-6f163d175c98 /home/mj/sdc1 ext3  exec,relatime  0  2
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


UPDATE:  DOH, I cut and pasted the UUID for the sdb1 twice(once for the sdc1)!!!!  Bet that is it...

---

### Post by jerome1232 on 2008-12-15
As one poster previously said I find it easier to give the volumes labels, from then on they will get mounted at /media/*volumeName*. 

Here is a how-to about labeling partitions of various file systems, it says it's for usb disks but that actually doesn't matter.

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

