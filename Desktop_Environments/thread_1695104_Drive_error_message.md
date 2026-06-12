---
title: "Drive error message"
date: 2011-02-25
forum: Desktop Environments
---

### Post by skaramanger on 2011-02-25
Greetings,

Recently I noticed an error in a logwatch report:

```
  ata5.00: ST_FIRST: DRQ=1 with device error, dev_stat 0x7F ...:  1 Time(s)

```
I also found this post with similar errors in this post:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9623377](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9623377)

So I did a grep of my daily messages:

```

[my-desktop ~]$ dmesg | grep ata5
[    0.970829] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xfc00 irq 14
[    1.152997] ata5.00: ATAPI: _NEC DVD_RW ND-2500A, 1.06, max UDMA/33
[    1.153064] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc0000000) ACPI=0x701f (60:600:0x13)
[    1.191533] ata5.00: configured for UDMA/33
[my-desktop~]$

```

Its my CD/DVD drive.  First off that drive does not have any hardware in it and this is the first time I have seen this kind of an error message for this drive.  So is any kind individual could explain to me what this error message means that would be great!  Secondly, do I need to be concerned about it?

Thanks,

skaramanger

---

