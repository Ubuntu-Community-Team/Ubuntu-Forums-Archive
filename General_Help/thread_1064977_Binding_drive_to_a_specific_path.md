---
title: "Binding drive to a specific path"
date: 2009-02-09
forum: General Help
---

### Post by viraptor on 2009-02-09
Hi,
I wanted to set up my fstab so that my external disk is always mounted in the same place -> /mnt/XXX

What I've got now is:
```
UUID=297da18a-fdc3-4c98-a538-ea478bb57c2f /mnt/XXX ext3 user,noatime,rw,exec,sync,auto 0 0
```

And sure, when I do `mount -a`, I have it mounted where I want. But what I wanted to achieve is that the disk automatically gets mounted in the right place after it's connected - like other disks that create new directories in /media/... How do I do that?

It's a standard disk in an external usb case.

---

