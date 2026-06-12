---
title: "How to rename partitions, including usb drives"
date: 2008-12-11
forum: General Help
---

### Post by slayer^_^ on 2008-12-11
_This guide is for editing FAT16/FAT32, NTFS, ext2/ext3, JFS, ReiserFS, and XFS filesystem partition labels._

**Basics**

There are 6 programs used to label a partition - the program used depends on the partition's filesystem type:

For FAT16 and FAT32 partitions, use _mtools_.

For NTFS partitions, use _ntfsprogs_.

For ext2 or ext3 partitions, use _e2label_.

For JFS partitions, use _jfs_tune_.

For ReiserFS (v3) partitions, use _reiserfstune_.

For XFS partitions, use _xfs_admin _

By default, external drives automount at /media/disk then /media/disk-1 and so on. This is not very helpful when trying to find the drive you are looking for, especially if you have multiple devices plugged in.

Labeled devices that automount will be mounted in the /media directory using their label as the mount point, /media/<label>. ex: /media/my_external .

When creating labels, be sure that the new mount point (based on the label) does not already exist since hal's automount function creates the directory when it mounts the device.

This guide is primarily for external drives such as USB hard drives, USB flash drives, and flash memory cards. You can label internal disks, but to change their mount points, use MoveMountpointHowto which uses the file called Fstab.
[B]
Identify your Partition[/B]

Plug in your USB device (if you need to rename an USB device)and list your partitions with:

```
sudo fdisk -l
```

You can also list your mounted devices and their descriptions with:

```
mount
```

For the rest of this tutorial we will use the following:

<device> = your device /dev/sdxy, ex: /dev/sdb1

<label> = your desired (new) label, ex: my_external 

**Install the Labeling Program**

Based on the package names listed above for each filesystem type, install the correct package for your partition:
```

sudo apt-get install <package>
```

Here are all the different ones:
```

sudo apt-get install mtools

sudo apt-get install ntfsprogs

sudo apt-get install e2fsprogs

sudo apt-get install jfsutils

sudo apt-get install reiserfsprogs

sudo apt-get install xfsprogs
```

or install the appropriate package from Synaptic.
[B]
Unmount the Partition[/B]

Partitions generally need to be unmounted before you can fiddle with them, so unmount the partition of the device you want to change the label for:

```
sudo umount <device>
```

ex:

```
sudo umount /dev/sdb1

```
If it was automounted, you can also unmount the drive by right clicking the desktop icon and clicking Unmount (or Eject in some cases).
[B]
Changing the Label[/B]
[U]
FAT16 and FAT32[/U]

These filesystems are most often found on USB thumb drives, flash cards (like for a camera or cell phone), and older external USB hard drives.
Check the current label
```

sudo mlabel -i <device> -s ::
```

ex:

```
sudo mlabel -i /dev/sdb1 -s ::
```

Note that we're using the special "::" drive which allows us to specify the device descriptor on the command line; otherwise we'd have to edit ~/.mtoolsrc to assign a drive letter.

If you get a message like this:

Total number of sectors (7831520) not a multiple of sectors per track (63)!

You can easily ignore the check by running this command:

```
echo mtools_skip_check=1 >> ~/.mtoolsrc
```

Change the label
```

sudo mlabel -i <device> ::<label>
```

ex:

```
sudo mlabel -i /dev/sdb1 ::my_external
```

**NTFS**

This filesystem is most often found on external USB and firewire hard drives or other Windows formatted disks.
Check the current label

```
sudo ntfslabel <device>
```

ex:

```
sudo ntfslabel /dev/sdb1
```

Change the label

Note: 128 characters maximum.

```
sudo ntfslabel <device> <label>
```

ex:

```
sudo ntfslabel /dev/sdb1 my_external
```

Ubuntu caches the drive's label so to see full affects of the change it is not enough just to umount and mount it again, the you should umount, remove, put back, mount again.

**ext2 and ext3**

These filesystems are most often found on linux formatted drives.
Check the current label
```

sudo e2label <device>
```

ex:

```
sudo e2label /dev/sdb1
```

Change the label

Note: 16 characters maximum.

```
sudo e2label <device> <label>
```

ex:

```
sudo e2label /dev/sdb1 my_external

```

**JFS**

These filesystems are most often found on IBM and some linux formatted disks.
Check the current label

```
sudo jfs_tune -l <device>
```

ex:

```
sudo jfs_tune /dev/sdb1
```

Change the label

Note: 16 characters maximum.

```
sudo jfs_tune -L <label> <device>
```

ex:

```
sudo jfs_tune -L my_external /dev/sdb1
```

**ReiserFS (v3)**

This filesystem is most often found on linux formatted disks.

Note: this could work with ReiserFS 4 too, I have not tried.
Change the label

Note: 16 characters maximum.

```
sudo reiserfstune -l <label> <device>
```

ex:

```
sudo reiserfstune -l my_external /dev/sdb1
```

**XFS**

This filesystem is most often found on UNIX formatted disks.
Check the current label

```
xfs_admin -l <device>
```

ex:

```
xfs_admin -l /dev/sdb1
```

Change the label

Note: 12 characters maximum.

```
sudo xfs_admin -L <label> <device>
```

ex:

```
xfs_admin -l my_external /dev/sdb1
```

Verify the Change

Now for the easiest part: unplug the drive, wait a second, then plug it back in. It should appear on your desktop with the new label and have its new mount point. 

DISCLAIMER: all the informations above are taken from the Ubuntu help site : [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

