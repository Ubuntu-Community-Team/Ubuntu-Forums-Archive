---
title: "usb drive not automounting"
date: 2009-01-03
forum: General Help
---

### Post by ilovelinux33467 on 2009-01-03
Hi when I plug in my external drive it doesn't auto mount. manually mounting it works fine via sudo mount or doing gnome-mount but I am just wondering why the automount is not working. The external drive is a LaCie 160 GB Hard Drive formatted as FAT32 which is vfat in linux. Here is the part of dmesg which says its reconized:

```

[ 2492.888274] sd 11:0:0:0: [sdb] Write Protect is off
[ 2492.888284] sd 11:0:0:0: [sdb] Mode Sense: 00 38 00 00
[ 2492.888292] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 2492.888307]  sdb: sdb1
[ 2492.894704] sd 11:0:0:0: [sdb] Attached SCSI disk
[ 2492.896002] sd 11:0:0:0: Attached scsi generic sg1 type 0
[ 2581.773150] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 295
[ 2701.778047] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 295
[ 2821.789222] ===>rt_ioctl_giwscan. 2(2) BSS returned, data->length = 204

```

I should also point out that I am using a custom kernel because I am using the asus eee pc 1000H.

The automount was working a while a go but now it has just stopped. Any suggestions? thanks. :)

---

