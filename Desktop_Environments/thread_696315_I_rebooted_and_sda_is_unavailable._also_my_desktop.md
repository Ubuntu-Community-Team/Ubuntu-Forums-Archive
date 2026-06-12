---
title: "I rebooted and sda is unavailable. also my desktop background reseted to default"
date: 2008-02-13
forum: Desktop Environments
---

### Post by einherier on 2008-02-13
I rebooted and the drive that allows me to access the partition of my computer that is windows is not there....just a blank space....also I had a really cute pic of me and my lady friend and it changed to one of the standard beige backgrounds.

Any ideas?

tanks much

---

### Post by Sir.Babau on 2008-02-13
Can you post your fstab file? Open a terminal and type:

gedit /etc/fstab

Then paste the text into a post.

Is your Windows partition formatted as fat32 or NTFS?

---

### Post by einherier on 2008-02-14
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=84b59e50-c329-4d08-a5a8-0ae189d2e783 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=965206065205EC35 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=157edf77-3170-4cd4-a3ae-f91aff1c822f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

Absolutely NTSF

---

### Post by Sir.Babau on 2008-03-10
Try replacing UUID=965206065205EC35 with /dev/sda1 so that the line looks like this:

```

# /dev/sda1
/dev/sda1 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1

```

---

