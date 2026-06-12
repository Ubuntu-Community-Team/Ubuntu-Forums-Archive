---
title: "All files 4GB?"
date: 2011-06-13
forum: Desktop Environments
---

### Post by awacs on 2011-06-13
I'm working from a Lucid live CD (desktop HD crash ...) and when viewing files on another server, *all* files, no matter what, are reported as 4.0 GB. As you might imagine, this puts a crimp in things. Can anyone suggest a workaround? Copying the files to the ubuntu desktop doesn't work - "not enough space".

Thanks!

---

### Post by tgalati4 on 2011-06-14
If the data is important, then buy a second disk.  Boot the LiveCD and open a terminal:

sudo cp /dev/sda /dev/sde

Change your device designators (your second disk may not be sde) to the correct ones.

Now work only on the copied disk:

Still in the LiveCD session: (you must be connected to a network)

sudo apt-get install testdisk
man testdisk
man photorec

This is a two-step process.  First testdisk will look over the file structure and try to repair it.  My guess is your inodes table got blown away so the data is still on the disk, but there is no valid index to find it.  The 4GB file size is probably the kernel's response to invalid file sizes being retrieved from disk.

If test disk works and you can navigate through your directories and files, then simply swap disks.  Use:

blkid

to get the UUID's of your disks and change them to the new one in grub or wherever they are used (like /etc/fstab).

If the new disk is bigger than the old disk (likely), then use gparted to either expand the existing partition to use the entire disk, or make an additional partition for data.

The second step happens if testdisk fails miserably.  Sometimes the partition table and file index cannot be resurrected.  Photorec is the program that simply looks at the raw data and uses intelligent guesses as to data type and then copies the files it finds to another disk.  This means you need a YARLD--Yet Another Really Large Disk--or a bunch of flash drives to capture the files that photorec recovers.

If your original hard disk (the one that crashed) is making weird noises and really seems to be on it's last legs, then use photorec to recover files right away, since the drive may not survive a complete copy process.  You still need a second empty drive to capture the files that photorec recovers.

If all this sounds like a lot of work,

it is.

---

