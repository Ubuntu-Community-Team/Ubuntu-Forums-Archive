---
title: "osprober attempting to mount EXTENDED partitions?"
date: 2014-10-17
forum: Desktop Environments
---

### Post by prshah on 2014-10-17
My dmesg is spammed with error messages about mounting /dev/sda3;
 sda3 is an EXTENDED partition that should NOT be mounted!

It's not causing any problems right now; (maybe a slightly delayed boot); but I find this error message unsettling:

> ```

Oct 11 00:06:26 xxx os-prober: debug: running /usr/lib/os-probes/50mounted-tests on /dev/sda3
Oct 11 00:06:26 xxx kernel: [ 5104.616620] EXT4-fs (sda3): unable to read superblock
Oct 11 00:06:26 xxx kernel: [ 5104.618643] EXT4-fs (sda3): unable to read superblock
Oct 11 00:06:26 xxx kernel: [ 5104.620527] EXT4-fs (sda3): unable to read superblock
Oct 11 00:06:26 xxx kernel: [ 5104.622701] FAT-fs (sda3): bogus number of reserved sectors
Oct 11 00:06:26 xxx kernel: [ 5104.622709] FAT-fs (sda3): Can't find a valid FAT filesystem
Oct 11 00:06:26 xxx kernel: [ 5104.629358] XFS (sda3): Invalid superblock magic number
Oct 11 00:06:26 xxx kernel: [ 5104.634171] FAT-fs (sda3): bogus number of reserved sectors
Oct 11 00:06:26 xxx kernel: [ 5104.634179] FAT-fs (sda3): Can't find a valid FAT filesystem
Oct 11 00:06:26 xxx kernel: [ 5104.662930] sda3: rw=16, want=3, limit=2
Oct 11 00:06:26 xxx kernel: [ 5104.672308] hfs: can't find a HFS filesystem on dev sda3

```

Can I safely assume it's an osprober issue, or should I check deeper? No other ATA/HDD errors show up anywhere.

Any way to PREVENT osprober attempting to mount an EXTENDED (logical partition container) partition?

Regards,

---

### Post by oldfred on 2014-10-17
Post these, have not seen os-prober attempting to read an extended parition:

sudo parted -l
sudo fdisk -lu
mount
 sudo blkid -c /dev/null -o list

---

### Post by prshah on 2014-10-18
> **oldfred said:**
> 
sudo parted -l
sudo fdisk -lu
mount
 sudo blkid -c /dev/null -o list

Thank you for your reply.

These commands do nothing other than list the partitions and mounts.

It may have some diagnostic value; but it does nothing to osprober.

Thanks anyway.

Regards,

---

