---
title: "External hard drive issues.."
date: 2006-01-02
forum: General Help
---

### Post by mattsadd on 2006-01-02
Hello!  I'm trying to set up a Seagate 200GB Ultra ATA hard drive in a Nexstar 3 External Enclosure.  I can format and partition the drive with seeming success, but can't mount it.  Also, the detected size varies; right now it's 96GB, but it's also been 106, 126, 189, 134, etc etc....

I have formatted and reformatted in ext2, ext3, and fat32 several times.  I just want one big partition because I'm going to store audio and video files on it.

When I try to mount using-
matthew@ripcord:/media$ sudo mount -t ext3  /dev/sda1 external

I get-
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail says-
[4392433.710000] XFS: SB validate failed
[4392496.134000] FAT: Filesystem panic (dev sda1)
[4392496.134000]     invalid access to FAT (entry 0x0bfffbf8)
[4392496.134000]     File system has been set read-only
[4392504.562000] HFS+-fs: unable to find HFS+ superblock
[4393374.216000] FAT: Filesystem panic (dev sda1)
[4393374.216000]     invalid access to FAT (entry 0x0bfffbf8)
[4393374.216000]     File system has been set read-only
[4393771.120000] HFS+-fs: unable to find HFS+ superblock
[4393782.723000] VFS: Can't find ext3 filesystem on dev sda1.

Currently it is formatted as ext3, but any help with ext2 or FAT32 is also appreciated.

thanks!

---

### Post by Sef on 2006-01-04
Take a look at this thread and see if it helps you:

[http://ubuntuforums.org/showthread.php?t=108744&highlight=External+hard+drive]("http://ubuntuforums.org/showthread.php?t=108744&highlight=External+hard+drive")

---

### Post by shane2peru on 2006-01-04
If that doesn't help, post back, and I will try and help.  I just successfully formatted a NEW Western Digital 160GB IDE harddrive using a Laptop and external enclosure.  Let me say that Linux saved the day when XP couldn't/wouldn't do it.  It only took me 2 weeks.  I had "successfully" formatted it several times before it actually worked.

Shane

---

### Post by CarlFK on 2006-01-05
show the output of 
$ sudo fdisk -l

---

### Post by thread on 2006-01-05
CarlFK, I'm helping him out with the drive. The fdisk -l output follows:

Disk /dev/sda: 103.0 GB, 103078690304 bytes
251 heads, 63 sectors/track, 12731 cylinders
Units = cylinders of 15813 * 512 = 8096256 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       12731   100657620   83  Linux

Again, this is a 200Gb drive, but is only showing about half there. This is after creating the single partition in fdisk, using the defaults so as to expectedly take up the entire drive... and it still refuses to mount even with the -t flag as described in the original post.

I've never seen a usb drive be so stubborn. What gives?

---

