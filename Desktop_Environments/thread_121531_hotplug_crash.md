---
title: "hotplug crash"
date: 2006-01-25
forum: Desktop Environments
---

### Post by mjurce on 2006-01-25
I remove the service hotplu to prevent the system crash on boot.
But now  ubuntu can't detect cdroom.

---

### Post by trevorv on 2006-01-25
If you've removed hotplug, it won't be detected automatically, you need to mount it yourself with a command like

sudo mount /dev/cdrom /mnt/cdrom

---

### Post by mjurce on 2006-01-26
I have not the device /dev/cdrom, the output of my fstab:

/dev/sda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


I haven't too /dev/scd0  in /dev.

---

