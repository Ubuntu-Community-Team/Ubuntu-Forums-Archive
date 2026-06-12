---
title: "Mount LVM partitions in fstab from another linux distribution"
date: 2005-12-29
forum: General Help
---

### Post by BORTKOMMEN on 2005-12-29
My ubuntu breezy is on hdc and debian sarge on hdb. Both are partitioned in the same manner like this:

hdb/c1   / with ext3
hdb/c2   /boot with ext3
hdb/c3   as LVM where there are following partitions with ext3:

home
tmp
var
usr
usr/local
swap

In Debian I configured fstab and inserted Ubuntu's / and /boot partitions and their icons popped up nicely on the desktop and I have now read/write access to them.

The problem is how to access those LV partitions in Ubuntu on hdc3, and vice verse to access Debian logical volumes on hdb3 from Ubuntu.

I have not found any document or manual how to configure LVM in fstab, so if you have any idea, let me know.

---

### Post by elglas on 2006-01-02
I would like to know this aswell

---

### Post by schilcha on 2006-01-02
LVM-partitions are configured in fstab the same way as normal partitions. All you need is to supply the correct device.

Here's a line from a non-ubuntu system:
> 
/dev/system/var /var    reiserfs        defaults 1 2

"system" is the name of volume group and var is the name of the logical volume (and the mount-points).

If you have two different volume groups (one from debian and one from ubuntu), the corresponding partitions (logical volumes) are in the respective subdirectories in /dev. If you can't remember the names, try "sudo vgscan" -- it'll give you a list of all active volume groups. "sudo lvscan" will give you a list of all logical volumes in the volume groups.

Good Luck!

---

