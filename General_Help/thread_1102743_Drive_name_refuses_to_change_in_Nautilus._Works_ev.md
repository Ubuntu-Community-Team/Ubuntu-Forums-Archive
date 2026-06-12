---
title: "Drive name refuses to change in Nautilus. Works everywhere else"
date: 2009-03-22
forum: General Help
---

### Post by CK05 on 2009-03-22
Hi there.

I've tried millions of threads and this is my last resort as I can't get this to work on my own. 

Basically I've got a sata NTFS drive that won't change names in Nautilus, but it has the right name everywhere else (Gnome-Do, Banshee even Sudo Nautilus all see it's proper name)

fdisk:
> 
[B]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2ad423a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS[/B]

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08570856

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       14216   114189988+  83  Linux
/dev/sdb2           14217       14593     3028252+   5  Extended
/dev/sdb5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x108a95f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001    7  HPFS/NTFS



sda1 is the drive in question. 

fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6c0c924a-fbcb-4a4d-9b98-9869cd9a6af1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=46a2d3b8-ef19-4508-be4d-1586847299a5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
**/dev/sda1 	/media/Music ntfs defaults,umask=007,gid=46 0 0**
/dev/sdc1	/media/Storage ntfs defaults,umask=007,gid=46 0 0  

Go easy, despite my join date I am a noob! Cheers.

---

### Post by CK05 on 2009-04-03
I'm sorry I still can't get this to work. Everywhere on my computer it refers to this drive as Music. 

But Nautilus sees the wrong name and I can't change it. Surely this has to be simple step to rename a drive!

---

### Post by mb_webguy on 2009-04-03
Nautilus uses the [drive label]("https://help.ubuntu.com/community/RenameUSBDrive"), not the mount point.

---

### Post by CK05 on 2009-04-03
Thank you very much.

---

### Post by mb_webguy on 2009-04-03
No problem.

By the way, internal drives really shouldn't be mounted under the /media directory.  The /media directory is for removable media, so internal drives mounted under /media will be treated as such, which may have unintended undesirable consequences.  A better place to mount internal drives not used for a specific purpose is under the /mnt directory.

---

### Post by CK05 on 2009-04-03
But they're SATA drives? I thought this was normal for them to be removable.

Edit: I mounted them to the /mnt but the two drives I have don't show up in the Tree view in Nautilus like they did when they where mounted to /media. 

Is this normal? Is there a way to link them again so they show up in the tree view?

---

### Post by mb_webguy on 2009-04-04
Hrm... sounds like you're still stuck a bit in the Windows mindset when it comes to mounting things.

In Windows, each partition on each drive is mounted separately, and assigned a drive letter.  Your main hard drive partition is C, the next is D, etc.  The filesystems for each partition are kept separate from each other.  So if you have four partitions, you'd have four drive letters, each representing a different filesystem.

Linux, on the other hand, has what's called a unified file system.  Linux really doesn't care about the physical location of storage.  The filesystem is what it is regardless of how many separate partitions or drives might be used, because partitions are mounted as directories within the filesystem.  And they can be mounted as *any* directory within the filesystem.  You could have the /usr directory on a separate partition, and /home on another.  Or you could mount a partition as /home/yourusername/Music, so your user account has access to a greater amount of storage for music.

Generally, this is the way partitions are mounted in Linux -- as some existing directory, for some specific purpose.  However, it's perfectly acceptable to mount a partition for general use.  That's what the /mnt directory is for -- at least on Ubuntu.  The /mnt directory was originally intended for the purpose now used by /media, which is to mount removable storage.  But on systems that use the /media directory for this, /mnt is instead a place to generically mount permanent storage.

For example, on my old laptop, I dual-boot with Vista, and have a data partition where I keep all of my data, which is shared between Windows and Ubuntu (i.e. it's mounted in both OSes).  I didn't want to simply use it as my /home directory in Ubuntu, because that would expose my Ubuntu user configuration files to Windows.  So instead, I mounted the partition as /mnt/data, and then replaced the Music, Pictures, Documents, and other directories under my home directory with symlinks that point to these directories under /mnt/data, the shared data partition.  That way, my Documents folder in Vista is the same as my Documents folder in Ubuntu, etc.

Just as Linux doesn't care where storage is physically located, it doesn't really care what type of storage it is.  The only difference between an IDE drive and a SATA drive as far as Linux is concerned is the device ID associated with it.  IDE drives get a device id that starts with "hd" and SATA drives get a device id that starts with "sd".  That's it.  And since Linux doesn't treat them differently, there's no reason why you should.

As for the thing about Nautilus...  The partition was showing up separately in Nautilus when you had it mounted under /media precisely because you had it mounted under /media.  Nautilus saw it as removable storage, and removable storage is listed in the Nautilus Places menu.  But from what you've said, what you have *isn't* removable storage, and shouldn't be treated as such.  An internal drive should be mounted somewhere in the filesystem, and would thereafter be treated as just another directory.  To access the information on that partition, you'd either navigate to that directory, or create symlinks that point to that directory and navigate to them.

---

### Post by ibuclaw on 2009-04-04
> **mb_webguy said:**
> The only difference between an IDE drive and a SATA drive as far as Linux is concerned is the device ID associated with it.  IDE drives get a device id that starts with "hd" and SATA drives get a device id that starts with "sd".  That's it.  And since Linux doesn't treat them differently, there's no reason why you should.
Correction:

IDE drives get a device id that starts with "hd" and **SCSI drives** get a device id that starts with "sd".

To find out which hard drive you have:
```
cat /proc/partitions
```
If the hard disk **Major** number is of one of the following:
*3 22 33 34 56 57 88 89 90 91*
Then you have an IDE drive.

Else if one of these:
*8 65 66 67 68 69 70 71*
Then you have a SCSI drive.

Most modern PCs will have a SCSI drive, as identified by the Major number **8**.


And yes, all mountpoints in /media are treated as removeable mediums by Nautilus.

Regards
Iain

---

### Post by mb_webguy on 2009-04-06
Oops... My slip was showing.  And well caught, tinivole.  Yes, I did confuse my SATA with my SCSI there.  I'm sure one day we'll all die smothered under an avalanche of acronyms -- that's AoA, btw, which rather conveniently resembles a snowball between two icy peaks...

---

### Post by CK05 on 2009-04-07
Sorry for the late response and thanks for the posts guys.

mb_webguy, reading that was fantastic. You just opened up another door of possibilities that I wasn't aware of before and you explained it so well. I had no idea it worked like that. 

Thanks for taking the time to help me out, I appreciate it!

---

### Post by vsiege on 2009-04-11
After reading this great thread I feel the need to move my mount point from /media to /mnt. I am running 8.10 only. I have a small amount of data on the drive currently (which I have backed up). How can I swtich the drives mount point?

---

