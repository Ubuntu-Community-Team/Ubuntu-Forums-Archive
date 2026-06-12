---
title: "moving ubuntu to another HD"
date: 2006-09-30
forum: Desktop Environments
---

### Post by sblanzio on 2006-09-30
Hello!

Initially, a month ago, I installed ubuntu on a secondary harddisk with only 10Gb available. Now, because of free space issues, I'd like to move the entire distro to my primary HD, hda, where I can manage 60Gb.

What is the easier (and safer) way to do that?

thank you in advance!

sblanzio

---

### Post by aysiu on 2006-09-30
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by sblanzio on 2006-09-30
Thank you for this link, it's very useful... i just don't understand few steps...

could you please tell me how can i do step-by-step?

I have several questions about this process...

do i need to install another ubuntu distro in hda1 to be able to backup hdc1?

then I don't think it is possible to restore to a mounted partition, so what can I do? Do I have to boot from hdc to restore the backup file to hda? if so, how can I switch easily between hdc boot and hda boot?

however, how can I tell to the bootloader to load the new partition then?

is it necessary to edit any file in my distro to be compatible with my new HD?

More, I have a linux-swap partition on hdc3.. how can I create a new swap partition and teach ubuntu to point that?

I know all this can be confusing... I'm sorry. I'll try to explain simply my aims...

- hdc1 is my ubuntu distro.
- I need to move hdc1 and hdc3 to hda.
- I'll completely format hda with a new big linux partition.
- I'm not interested in hdc2 that is old partition.
- I need to create a new swap partition in hda.
- hdb is maybe too small to be useful, however it shouldn't be interested in this operation.

Follows my  "sudo fdisk -l" response:

```

Disk /dev/hda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3650    29318593+   c  W95 FAT32 (LBA)
/dev/hda2            3651        7299    29310592+   f  W95 Ext'd (LBA)
/dev/hda5            3651        7299    29310561    b  W95 FAT32

Disk /dev/hdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         783     6289416    b  W95 FAT32

Disk /dev/hdc: 15.0 GB, 15020457984 bytes
255 heads, 63 sectors/track, 1826 cylinders
Units = cilindri of 16065 * 512 = 8225280 bytes

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1533    12313791   83  Linux
/dev/hdc2            1534        1686     1228972+  83  Linux
/dev/hdc3            1687        1826     1124550   82  Linux swap / Solaris
```

thank you again

---

### Post by aysiu on 2006-09-30
You'll need to use a live CD so that no partition is mounted except the one you want to copy.

So you'll boot up the live CD, mount /dev/hdc and copy that partition to /dev/hda

There's a feature in PartImage to back up Grub, too, but I've never used it.

I did write that HowTo, but I'm not really a PartImage expert. You may find some helpful information on this page, though:
[http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)

---

