---
title: "Unable to make LVM snapshots"
date: 2009-04-01
forum: General Help
---

### Post by texas1emt on 2009-04-01
I'm currently running Ubuntu 7.10 and I get this error when I try to make a snapshot with lvcreate:

```
# lvcreate -s -n testing_snap -L5G /dev/volumes/testing_root
  device-mapper: create ioctl failed: Device or resource busy
  device-mapper: reload ioctl failed: No such device or address
  Failed to suspend origin testing_root
```

I've made many snapshots from this volume before, but I am unable to now.  It will actually make a /dev/volumes/testing_snap logical volume, but it's not usable at all.  If you remove the snapshot volume and list what's in /dev/mapper, you see this:

```
# ls -al /dev/mapper/volumes-testing_*
brw-rw---- 1 root disk 253,  7 2009-03-25 11:06 /dev/mapper/volumes-testing_root
brw-rw---- 1 root disk 253, 10 2009-03-31 05:17 /dev/mapper/volumes-testing_root-real
brw-rw---- 1 root disk 253, 46 2009-03-31 05:17 /dev/mapper/volumes-testing_snap-cow
brw-rw---- 1 root disk 253, 45 2009-03-25 11:06 /dev/mapper/volumes-testing_swap
```

The real and cow (copy on write) LV's still exist.  I can remove the nodes manually with rm, but that has no effect on the snapshot issue.  Does anyone have any ideas?

---

