---
title: "Out of room and need to shrink partitions."
date: 2006-03-23
forum: Desktop Environments
---

### Post by Sef on 2006-03-23
I can't get into GDM because the my home patition is too small.  (See Below.)

What is the best way to combine hda3 (my home partition) and hda5?

Partition           File System           Size               Used                 Unused              Flags

/dev/hda1        ntsf                        4769              4426                343                      boot

/dev/hda2        fat32                      4769                  32              4737

/dev/hda3        ext32                     3812              3711                 101

/dev/hda4        extended               5733               ----                   ----

/dev/hda5        ext32                     4769                756                4013

/dev/hda6         swap                      1004               ----                  -----


1.3 GB Celeron, 512 Memory

---

### Post by taurus on 2006-03-23
You can use gparted to resize your partitions and by the way, I don't think I have ever seen ext32 before!  Is it ext2 or ext3?

---

### Post by Sef on 2006-03-23
> I have ever seen ext32 before! Is it ext2 or ext3?

oooppppsss.  ext3.

thanks I was thinking of that, but didn't know if there was a better way or not.  Thank you for your help.

---

### Post by arctic on 2006-03-23
Make a backup of all important files before you resize your partition. Don't touch the existing first sector of the linux partition, only modify the stuff after the first sector, otherwise you will loose all your data.

---

### Post by Sef on 2006-03-23
> Make a backup of all important files before you resize your partition.

How do I make a back up with Ubuntu's Live CD?  I don't see GnomeBaker on it nor anything else that I can burn a disc with.

> Don't touch the existing first sector of the linux partition, only modify the stuff after the first sector, otherwise you will loose all your data.

Am planning to delete /dev/hda5  and increase the size of /dev/hda3.

Thank you.

---

### Post by arctic on 2006-03-23
[QUOTE=Sef]How do I make a back up with Ubuntu's Live CD?  I don't see GnomeBaker on it nor anything else that I can burn a disc with.
.[/QUOTE] There should be Nautilus burner available (nothing great, but it works). Open Nautilus, select the places menu and there should be a burner option available. You can install a burner probably on your base system, too. Have you tried to free up some space already, e.g. by cleaning your cache?

apt-get clean cache

This might give you enough free space for downloading e.g. xcdroast or gnomebaker.
You can also use live-CDs like Knoppix or Kanotix. They have K3B included.

---

### Post by Sef on 2006-03-24
>  There should be Nautilus burner available 

Can't figure out how to access my files on the hard drive with it.  See if I have Knoppix still around somewhere.

> Have you tried to free up some space already, e.g. by cleaning your cache?

apt-get clean cache

Get a message saying:

E: Could not open locked file /var/cache/apt/archive/lock open (13 Permission denied)

E: Unable to lock the download directory.

**Gparted message:**

Unable to delete partition

Unable to unmount any partitions having a number higher than 5.

hda 5 and 6 are both extended partitions.  

What should I do to fix these problems?

---

### Post by Sef on 2006-03-24
Update:

hda6 is mounted; how do I unmount it?

Update 2:

tried to umount via the terminal (umount -v /dev/hda6: got this message -- /dev/hda6 is not mounted (according to mtab.)  

However, under Gparted it is locked.

---

### Post by plors on 2006-03-24
start gparted from its own [livecd]("http://gparted.sourceforge.net/livecd.php"). This has 2 advantages:
- no problems with mounted partitions
- always the latest software 

btw, the iso is only 25 MiB :)

---

### Post by Sef on 2006-03-24
> start gparted from its own livecd.

When I try and burn, i get a message saying that I need to insert a disk.  However, the disk is already in there.

---

### Post by plors on 2006-03-24
[QUOTE=Sef]When I try and burn, i get a message saying that I need to insert a disk.  However, the disk is already in there.[/QUOTE]

heh :) burning under ubuntu is out of my league, but i'm sure someone else can help you with this.

---

### Post by Sef on 2006-03-24
> start gparted from its own livecd. This has 2 advantages:
- no problems with mounted partitions
- always the latest software

btw, the iso is only 25 MiB 

Update:

1) Got gparted on its own disk.  

2) Wiped out my hda1 (a cracked copy of XP)

     a) have about 5.5 GB free
     b) changed to ext 3 now

3) But how do i transfer the free space to hda3?

---

