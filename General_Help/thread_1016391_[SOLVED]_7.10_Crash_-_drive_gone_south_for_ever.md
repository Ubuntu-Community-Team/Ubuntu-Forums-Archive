---
title: "[SOLVED] 7.10 Crash - drive gone south for ever?"
date: 2008-12-19
forum: General Help
---

### Post by djhmateer on 2008-12-19
Hi

My 7.10 box has been working for about 6 months.  Turned it on yesterday and up popped the BusyBox mode.

When I boot in recovery mode I see:

EXT3-fs error (device hda1): ext3_check_descriptors: Block bitmap for group 833 not in group (block 905969733)!
EXT3-fs: group descriptors corrupted
Mount:  mountaing /dev/disk/by-uuid/627234f0-84be-4db8-aeda-60eb4a0f24bb on /root
Failed: Invalid Argument

When I boot to Damn Small Linux:

fdisk -l
Disk /dev/hda 120GB blah blah
/dev/hda1	Linux
/dev/hda2	Extended
/dev/hda5	Linux Swap


fsck.ext3 /dev/hda1
Group descriptors look bad... trying backup blocks...
fsck.ext3: Filesystem has unsupported feature(s) /dev/hda1
e2fsck: Get a newer version of e2fsck

debugfs -w /dev/hda1
/dev/hda1: Can't read an block bitmap while reading block bitmap


Nothing on the box that isn't backed up.  

Opinion:  Should I give up, and throw away the hard disk?

Cheers

---

### Post by cdtech on 2008-12-19
You may want to give "testdisk" a shot at recovering the drive.
```
sudo apt-get install testdisk
```

---

### Post by djhmateer on 2008-12-19
Am trying that now.. can't boot into Ubuntu, even liveCD - just keeps dumping into BusyBox.  

So getting [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

which has testdisk in the install

Will post back results.

---

### Post by djhmateer on 2008-12-20
It worked!

Many thanks

---

