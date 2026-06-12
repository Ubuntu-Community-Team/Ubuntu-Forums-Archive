---
title: "Worst Nightmare come true.  Help"
date: 2005-10-26
forum: Desktop Environments
---

### Post by Mitch on 2005-10-26
I was looking for a way to start backing up my valuble files onto an extra hard disk I had.  I decided to use half of it for my windows and half of it for backup.  I knew that reinstalling windows would mess up my grub, but I'd been through it before.  

Long story short, I used a howto to get my grub back with the Ubuntu unstallation CD.  I tried it a couple of different ways and it didn't work.  One time I set my ubuntu partition to "/" and made sure it was not set to be formatted, interpreting the howto that way.  Big mistake.  I was staring at a screen installing the base system on this partition.  I thought about pulling the plug but thought maybe it would be ok.  

I finally got access to the drive by installing Ubuntu on what would have been the backup partition.  A ubuntu partition was mounted automatically.  It has a base system with nothing in the home folder.  My one ray of light is that this partition is only 218 MB.  When I access my old hard drive from windows I see a partition 
/boot" that is 218 MB and the rest (~240 GB) is unaccessable.  The whole partition before this mess was 250 GB.  

That partition had everything on it.  I'm freaking out.  Am I F'ed?  is there any kind of data recovery that can save me.  


More info: (sorry for the length)  Trying to boot off the other partitions in GRUB... 

The first entry (Ubuntu Breezy)  stops with a Kernal panic.  The second entry gets only to the terminal login and won't accept any login except root.  Maybe if there was some way to fix that kernal or to access that partition I would be saved.  I've tried mounting all the other partitions I can from my new, temp breezy install.  sda1 mounts automaticall (218 MB base install)  sda2 and sda5 won't mount.  

here is my etc fstab if it helps

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ext3    defaults        0       2
/dev/sdb1       /media/sdb1     vfat    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Sdb1 is a USB drive I happened to have in.  
Sorry if this is long or frantic, I'll edit it later if it's bad.  Any help?

*Running e2fsck on my screwed up partition (sda5) wouldn't work.  I tried using different superblocks, but to no avail.  I always got the error: e2fsck: "Bad magic number in super-block while trying to open /dev/sda5"

* I read somewhere that I could try to run mke2fs -S which would write a new superblock for me.  How destructive is this.  Would it even help?

* Here is some fdisk output:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          31      248976   83  Linux
/dev/sda2              32       30401   243947025    5  Extended
/dev/sda5              32       30401   243946993+  8e  Linux LVM

* I'm beginging to see that this LVM thing is what may really be killing me.  What have I done?

---

