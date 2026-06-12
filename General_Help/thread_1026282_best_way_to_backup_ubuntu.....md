---
title: "best way to backup ubuntu...."
date: 2008-12-31
forum: General Help
---

### Post by sr_guy on 2008-12-31
What would be the best pain-free way to backup an Ubuntu install as an image over samba, dvd-r, or usb stick? I'm interested in backing up everything rather then incremental backups of certain directories. 

I tried using clonezilla, and it backed up my configured ubuntu system to a 2gig file, but when I tested it and tried to restore from the image it created, Ubuntu would only boot to a grub screen. I've used different flavors of linux including Redhat, Mandrake, and Suse and all would successfully restore with the clonezilla image. Ubuntu has been the only Linux OS I've had an issue with restoring with Clonezilla. 

Again, I would like to make a complete image backup, and not single directories.

---

### Post by sofasurfer on 2008-12-31
I obsessed over backing up for quite some time. I finally learned how to use RSYNC and TAR. They worked fine for backing up, but they used up a ton of disk space. Actually creating a clone still eludes me.

I eventually settled for just dragging and dropping my important directories to a second hard drive. Things like /documents, /videos, /pictures, /music, /bookmarks and other important personnal files. I chose not to include the entire /home folder because theres a lot of stuff in there that just doesn't matter. I also save a copy of 'sources.lst'. I used to have to save fstab and interfaces but with Intrepid I do not need these. 

So now I have the actual folders in my file system and copies in my second hard drive. I then use the dmesg command to save a package list to the second drive. 

Now if I have a problem I can reinstall the base system in 20 minutes, most of which does not need my attention. Then I move the 'sources.lst' copy to /etc. Then I use DMESG with dselect to reinstall all the packages and configure them. Finally, if I need my personnal folders to be put into my file system I just drag n drop them. But usually I just leave them on the second hard disk. 

Reinstalling isn't even a chore anymore.

---

### Post by nivreial on 2008-12-31
What I'd do (but I'm not a frequent back-upper) is work with dd to make a clone of the HDD in another one. restoring is just using the same thing again.
Seems to fit you, as you want to keep everything safe.

---

### Post by sr_guy on 2008-12-31
My concern is that when restoring my backup, ubuntu won't boot. I would like to back it up into one single image that can be restored without having to reconfigure the mbr or anything else. In other words, a free possible backup/restore method as easy as ghost, but one suitable for linux.

My goal is not to have to reinstall the core ubuntu cd if something goes south... just restore the image.

Does anyone have an idea of why clonezilla isn't successful on ubuntu?

---

### Post by nivreial on 2008-12-31
> **sr_guy said:**
> My concern is that when restoring my backup, ubuntu won't boot. I would like to back it up into one single image that can be restored without having to reconfigure the mbr or anything else. In other words, a free possible backup/restore method as easy as ghost, but one suitable for linux.

My goal is not to have to reinstall the core ubuntu cd if something goes south... just restore the image.

Does anyone have an idea of why clonezilla isn't successful on ubuntu?
Possibly it doesnt support ext2 / ext3 or whatever format you use for your HDD?

---

### Post by rampageoberon on 2008-12-31
> **sr_guy said:**
> What would be the best pain-free way to backup an Ubuntu install as an image over samba, dvd-r, or usb stick? I'm interested in backing up everything rather then incremental backups of certain directories. 

I tried using clonezilla, and it backed up my configured ubuntu system to a 2gig file, but when I tested it and tried to restore from the image it created, Ubuntu would only boot to a grub screen. I've used different flavors of linux including Redhat, Mandrake, and Suse and all would successfully restore with the clonezilla image. Ubuntu has been the only Linux OS I've had an issue with restoring with Clonezilla. 

Again, I would like to make a complete image backup, and not single directories.

You might want to try remastersys. Its a nice and handy utility. You can find a guide at [http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

There is also PartImage or CloneZilla as mentioned (guides available at [www.dedoimedo.com](www.dedoimedo.com))

Hope that helps

---

### Post by bumanie on 2008-12-31
I personally like dd and creating a zipped image of the hard drive/partition. If you have a large enough external drive, you can do a clone of your present setup with dd commands too.

---

### Post by Zack McCool on 2008-12-31
Not sure why you are having a problem with clonezilla.  I have used it to backup and restore my Ubuntu system with no issues when changing hard drives, so I would think there are no distribution-specific problems with it...

Another option is dd.  You could boot to your Ubuntu LiveCD, mount the internal harddrive and an external USB drive to back up to.

Run this command:
```
 dd if=/dev/zero of=/mnt/sda1/tmp/disk_zero_fill.tmp bs=8M; rm -f /mnt/sda1/tmp/disk_zero_fill.tmp 
```

This command is assuming that you mounted your internal hard drive as /mnt/sda1, and that it has your tmp folder on it.  It then fills the disk with a huge file of all 0's, then deletes that file.  Just clears some junk off of the drive that you don't want in the image.

Now, unmount your internal drive.  It doesn't need to be mounted for the backup...

Next, run this command:
```
 dd bs=15M if=/dev/sda conv=sync,noerror | gzip -9 > /mnt/usb/images/sda.img.gz 
```

Again, this assumes a little bit, namely that your USB drive is at /mnt/usb and that there is a folder on it named images.  Adjust this to suit your needs.  What it will do, though, is copy a full image of your sda drive to a compressed (with gzip) image on the usb drive in that images folder.

---

### Post by sr_guy on 2008-12-31
When I installed ubuntu instead of selecting the "guided" option for partitioning I selected the option to use the "whole disk". Would that have caused an issue with the bckup method for clonezilla?

I also found the "simple backup method" utility for ubuntu and it seems to work good for sending bckups over ssh to another pc on the network. I'll have to check out dd as well as a method.

Also, if ubuntu is completed booted into the desktop and I try using any of the tools for backing it up wile booted up, won't it be screwed up because ubuntu has running process which cannot be backed up while booted? Therefore the bckp image will not restore the system totally to "boot right up" after restoring the image because it is missing files that could not be backed up because they were "in use"?

Here are how my partions are broken down:


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051927

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cb649

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    b  W95 FAT32

Disk /dev/sdc: 255 MB, 255852544 bytes
16 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x000186d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         976      249840    b  W95 FAT32

---

### Post by bumanie on 2008-12-31
Using the whole disk option should not have any effect on backing up. You are right to think that copying a mounted filesystem will potentially cause data to be copied that may be in an unstable state. As far as dd goes, the commands can be run off a live cd, hence the filesystem is not mounted. Never used clonezilla, but I think it runs off a live cd so the filesystem would not be mounted either.

---

### Post by sr_guy on 2008-12-31
Thank you to rampageoberon for suggesting remastersys. That seems to have done the trick with the full backup option. I tested the ISO image remastersys created in virtualbox and it booted right up with multiple options including the live and install options for the iso image. That seems to be the exact solution I was searching for.

---

