---
title: "ext3 partition on mdraid gone"
date: 2009-01-16
forum: General Help
---

### Post by Einmaliger on 2009-01-16
I thought it would be a good idea to use mdraid for higher data security, so I created a RAID 5 with an ext3 partition on it. It worked well until today, when suddenly the partition vanished. The system suddenly froze (which sometimes happens when I play videos, probably because of the NVidia drivers) and after a reboot the whole partition was gone.

Trying to mount it returns a frightening message:
> mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

The output of fsck is similar:
> fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Invalid argument while trying to open /dev/md0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

mdadm, however doesn't appear to see any problem. Running cat /proc/mdstat returns:
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb1[0](S) sdd1[2](S) sdc1[1](S)
      1465151808 blocks

unused devices: <none>

Is there any hope to get access to my 400 GB of data?

---

### Post by fjgaude on 2009-01-17
Okay, I'm sure everything is still there. Try this:

sudo mdadm --assemble --scan

If that doesn't work do it again but put a -f in the command.

Let us know what happens.

---

