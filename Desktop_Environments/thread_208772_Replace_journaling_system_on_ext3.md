---
title: "Replace journaling system on ext3"
date: 2006-07-04
forum: Desktop Environments
---

### Post by frup on 2006-07-04
in [http://www.ubuntuforums.org/showthread.php?t=208689](http://www.ubuntuforums.org/showthread.php?t=208689) i discovered my ext3 drive has lost its journal.. in the process to discover this i had to unmount it where it was temporarily mounted too. so now i can not mount it (to get the 26GB of data off it.) and i dont know how to add the journal to it.. 
if at the least someone could tell me how to get it mounted to i can back up the data on one of my other drives so i can format it i would be very happy..

thanks.. thanks to the people who helped in the other thread too.

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 4664 37463548+ 83 Linux
/dev/hda2 4665 4865 1614532+ 5 Extended
/dev/hda5 4665 4865 1614501 82 Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 155061 78150712+ 83 Linux

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdd1 * 1 9728 78140128+ 7 HPFS/NTFS

funny that should be ext3!!!

Filesystem Type Size Used Avail Use% Mounted on
/dev/hda1 ext3 36G 8.7G 25G 26% /
varrun tmpfs 379M 128K 379M 1% /var/run
varlock tmpfs 379M 4.0K 379M 1% /var/lock
udev tmpfs 379M 124K 379M 1% /dev
devshm tmpfs 379M 0 379M 0% /dev/shm
lrm tmpfs 379M 19M 361M 5% /lib/modules/2.6.15-25-386/volatile
/dev/hdb1 reiserfs 75G 31G 44G 42% /Linspire/reiserFS
/dev/hdd1 ext2 74G 26G 45G 37% /tmp/disks-conf-hdd1

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hdd1: clean, 6671/9781248 files, 7005515/19535032 blocks

laurent@ubuntu:~$ sudo mount /dev/hdd1
mount: wrong fs type, bad option, bad superblock on /dev/hdd1,
missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail or so


laurent@ubuntu:~$ dmesg | tail
[17179627.948000] NET: Registered protocol family 31
[17179627.948000] Bluetooth: HCI device and connection manager initialized
[17179627.948000] Bluetooth: HCI socket layer initialized
[17179628.016000] Bluetooth: L2CAP ver 2.8
[17179628.016000] Bluetooth: L2CAP socket layer initialized
[17179628.076000] Bluetooth: RFCOMM socket layer initialized
[17179628.076000] Bluetooth: RFCOMM TTY layer initialized
[17179628.076000] Bluetooth: RFCOMM ver 1.7
[17180387.556000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17188861.064000] ext3: No journal on filesystem on hdd1

---

### Post by frup on 2006-07-04
bump?

---

### Post by jimbob on 2006-07-04
Did you try to convert the fs to ext2 instead of ext3?  The only difference appears to be the journal so it shouldn't bother your data and you might be able to get it to then mount as ext2.  (mount -t ext2 /dev/hdd1) etc.

Several years ago in Red Hat (before I was baptized in Debian) I needed to do this and found an excellent 'how to' on the net.

If you google 'convert ext3 to ext2' there is a wealth of information out there.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

