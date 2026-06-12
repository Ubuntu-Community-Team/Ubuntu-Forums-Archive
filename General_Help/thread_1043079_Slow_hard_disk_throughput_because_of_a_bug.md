---
title: "Slow hard disk throughput because of a bug?"
date: 2009-01-18
forum: General Help
---

### Post by glotz on 2009-01-18
From my **dmesg**:
```
ata1: PATA max UDMA/100
ata1.00: max UDMA/100
ata1.00: limited to UDMA/33 due to 40-wire cable
ata1.00: configured for UDMA/33
```

**sudo hdparm -d /dev/sda** also produces weird results:
```
/dev/sda:
 HDIO_GET_DMA failed: Inappropriate ioctl for device
```

I'm using a 80-wire cable. Using Hardy. **uname -r**:
```
2.6.24-23-generic
```


How can I get my disks back to UDMA/100 throughput? Do you see similar behaviour?


.

---

### Post by glaze on 2009-01-18
There was a bug in some older kernels that would cause it to detect the cable wiring wrong, but it's fixed now, so just update your kernel.

---

### Post by glotz on 2009-01-18
You mean compile my own from kernel.org?

---

### Post by glotz on 2009-01-22
Bump. I have the latest Hardy kernel.

---

### Post by glotz on 2009-01-27
Anybody?

---

### Post by glotz on 2009-02-10
Once more unto the breach, dear friends...

---

