---
title: "Access windows partition"
date: 2009-02-28
forum: Desktop Environments
---

### Post by pgmuthukumar on 2009-02-28
Hi,
I have recently installed ubuntu 8.10 by dual boot logic.
Installing a dual-boot with Windows without partitioning
([http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)).

But I couldn't access the windows partitions from ubuntu and vice versa.  
Please help.

Thanks,

---

### Post by dariyoosh on 2009-02-28
> **pgmuthukumar said:**
> Hi,
I have recently installed ubuntu 8.10 by dual boot logic.
Installing a dual-boot with Windows without partitioning
([http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)).

But I couldn't access the windows partitions from ubuntu and vice versa.  
Please help.

Thanks,

Hello there:

For accessing Linux partition within windows you can use
explore2fs (among many other programs)

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

Normally by default, ubuntu supports NTFS read/write. I can read
my windows Vista partition from my linux partition (ubuntu 8.10)
without any problem. Maybe you forgot to mount those devices
from the nautilus window.

Regards,

---

### Post by windhorn on 2009-03-16
> **dariyoosh said:**
> Hello there:

For accessing Linux partition within windows you can use
explore2fs (among many other programs)

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

Normally by default, ubuntu supports NTFS read/write. I can read
my windows Vista partition from my linux partition (ubuntu 8.10)
without any problem. Maybe you forgot to mount those devices
from the nautilus window.

Regards,
I have a similar problem with 8.10 on my computer at home.  The filesystem is not mounted, and when I try to mount it (graphically) it gives a message that if I use windows I can't mount the drive; if not, I can use "force" to mount it but bad things may happen.  Probably Windows (2000) doesn't like anyone messing with its files while it is asleep.  Read only access would be fine.  Haven't tried fstab or shell "mount" command yet (I'll try to figure how to get into a shell tonight).

---

### Post by windhorn on 2009-03-16
Oops -- I found another thread that explains the reason for my problem (drive was not shut down properly), which seems to be different.

"Cannot Mount Volume - Ubuntu 8.04 - external usb ntfs drive" is the name if you are interested.

---

### Post by buldozerceto on 2009-03-16
if the drive is hibernated it won't be mounted unless you force it.

---

