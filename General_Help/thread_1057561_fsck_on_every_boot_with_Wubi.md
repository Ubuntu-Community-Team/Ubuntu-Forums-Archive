---
title: "fsck on every boot with Wubi"
date: 2009-02-01
forum: General Help
---

### Post by dreamingdarkness on 2009-02-01
I have Ubuntu installed through Wubi with Windows Vista.
I've been unable to figure out what I need to change in my fstab to keep it from running fsck on every boot. It says it's been something like 30 boots since last fsck, then proceeds with one.

Here is the output from cat /etc/fstab
Anyone have any thoughts?

Thanks in advance.


```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

```

---

### Post by tarot231 on 2009-02-22
On loopback filesystem, fsck seems not to reset mount count.
I solved with following:

sudo tune2fs -c -1 -i 0 /dev/loop0

---

