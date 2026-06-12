---
title: "Upgrading to a new Hard Drive."
date: 2009-04-21
forum: General Help
---

### Post by murmini on 2009-04-21
Is there a simple way to take a 20 Gig Hard Drive and copy it to a larger drive but maintain all of the existing data and existing user accounts.

---

### Post by Wayne_V on 2009-04-21
create the partitions you want on the new drive ('fdisk -l /dev/sda' to see your existing partitions).   Then 'dd' the existing to the new.  Then create the boot block (see [http://ubuntuforums.org/showthread.php?t=408436](http://ubuntuforums.org/showthread.php?t=408436)).

Or use mondorescue to create a disaster recovery backup and then restore to the new disk.

---

### Post by codeseer on 2009-04-21
Alternatively, [http://clonezilla.org/]("http://clonezilla.org/").

You could use the disk-to-disk imaging feature. It's basically dd with a frontend.

---

