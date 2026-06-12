---
title: "Problem running fsck...."
date: 2006-08-01
forum: Desktop Environments
---

### Post by Protege on 2006-08-01
Okay so I have 3 harddrives that run off a PCI to IDE controller card. I have one harddrive that runs off the motherboard IDE controller. The 3 that run off the controller card are storage while the one that runs through the motherboard is my OS installation. Well yesterday I wanted to try SUSE on it so I swapped the one OS harddrive with a blank one and began the install. Well during the install it told me I had hard drives arranged in a raid array. I click okay and aborted the installation, fearing it might destroy my storage drives. When I put my ubuntu install back in everything booted up just fine, except my 3 storage drives. Well I checked them and before they each had one partition and now they each have two, one small ext2 partition and 1 large unknown partition. Well I tried to run fsck off a knoppix 5.10 disk but I got this error.

```
knoppix@1[knoppix]:~$ sudo fsck /dev/hdf2
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/hdf2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```
Well I tried running e2fsck -b 8193 /dev/hdf2 and I got the same error back.

Can anyone help me please I really want to restore these drives as they have about 500 gb of data on them!

---

### Post by Protege on 2006-08-02
I do not want to be annoying, but I really need to know if there is a way for me to recover my 500 gb of data. Please if anyone can help I would appreciate it.

Thank you.

---

