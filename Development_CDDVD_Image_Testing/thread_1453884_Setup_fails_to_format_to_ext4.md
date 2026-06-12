---
title: "Setup fails to format to ext4"
date: 2010-04-13
forum: Development CD/DVD Image Testing
---

### Post by xslntx on 2010-04-13
Strange problem I've been having with Lucid, that I haven't encountered on any other distro.

When attempting to partition my striped, fakeraid array, it fails to format the partitions. Gparted doesn't even show any /dev/mapper devices. Both cfdisk and fdisk can't open the device. Any idea what's going on?

The installer sees the array just fine, and is able to actually partition it, but refuses to format. 

Listing the arrays with dmraid -ay returns the drives and partitions as it should.

---

