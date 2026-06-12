---
title: "ntfs partition not mounting"
date: 2008-12-14
forum: General Help
---

### Post by Josey on 2008-12-14
I recently reinstalled windows xp and now it isn't mounting the partition in ubuntu.  How do I go about fixing this?

---

### Post by graysky on 2008-12-14
```
$ sudo aptitude install ntfs-3g
```

Now edit your fstab and create an entry for that partition.

Here is mine for comparison (your file system and mount point are likely different):

```
/dev/sda2       /mnt/D          ntfs-3g defaults        0       0
```

You can reboot and it'll be there, or issue:

```
$ sudo mount /dev/sda2 /mnt/D
```

---

### Post by Josey on 2008-12-14
Thanks... I was able to mount it.  I'm a little confused though as my fstab and output of fdisk -l don't match up.

My fstab claims it's mounting /dev/hda1 - /dev/hda6
but fdisk claims my disk is /dev/sda1 - 6

Nowhere in fstab does it mention /dev/sda but the output of fdisk - l is as follows.  Can someone explain this to me?

```
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100       11862    54323797+  83  Linux
/dev/sda3           11863       38910   217263060    f  W95 Ext'd (LBA)
/dev/sda5           11863       38643   215118351   83  Linux
/dev/sda6           38644       38910     2144646   82  Linux swap / Solaris

```

and here is my fstab

```
# /dev/hda2
UUID=df869828-a90d-4d77-a41c-8b300c3bf557 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/hda5
UUID=3bcf7983-18aa-44ed-b17a-b2e8c717123c /home           ext3    defaults,relatime        0       2
# /dev/hda1
UUID=BAA02501A024C5AB /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/hda6
UUID=aa3eb47b-9490-48be-84ce-715bd167572f none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

---

### Post by graysky on 2008-12-14
Dunno... I would recommend that you use the ntfs-3g driver as it is more robust and extensively tested.

---

### Post by albinootje on 2008-12-14
The references to /dev/hda1 - /dev/hda6 in your /etc/fstab are not really used like that.
It does use the uuid for it. You can check that with :
ls -la /dev/disk/by-uuid/

Quite some time (kernels) ago, Linux used /dev/hda for the primary IDE disk, and /dev/sda for SCSI disk or usb disk.

After that the kernel started naming IDE disk /dev/sda and /dev/sdb too.

Personally i find that very confusing sometimes, and it can be dangerous if you're using a lot of machines in combination with usb disks and usb sticks.

---

