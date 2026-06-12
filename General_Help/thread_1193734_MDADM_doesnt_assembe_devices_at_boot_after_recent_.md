---
title: "MDADM doesnt assembe devices at boot after recent updates"
date: 2009-06-21
forum: General Help
---

### Post by irishdunn on 2009-06-21
Just updated my server, when I rebooted my md0 device wasn't started. I can start the device with 'sudo mdadm --assemble scan' and mount it with the mount command... but I would rather the device start when linux boots and mount itself with fstab.

please help!

---

### Post by Bachstelze on 2009-06-21
Add something like this to your [font="monospace"]/etc/mdadm.conf[/font]:

```

DEVICE /dev/sd[abc]1
ARRAY /dev/md0 devices=/dev/sda1,/dev/sdb1,/dev/sdc1
```

Of course replace with the correct device names.

---

### Post by irishdunn on 2009-06-21
My file already looks like this, I didnt add the devices to the array block yet:

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE /dev/sd[bcdef]1

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=5 UUID=44086b56:364386c6:613e2239:070da8c8
   spares=1

---

### Post by Bachstelze on 2009-06-21
> **irishdunn said:**
> My file already looks like this, I didnt add the devices to the array block yet:

All right, try adding them, then.

---

