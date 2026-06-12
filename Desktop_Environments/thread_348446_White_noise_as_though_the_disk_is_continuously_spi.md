---
title: "White noise as though the disk is continuously spinning all the time"
date: 2007-01-28
forum: Desktop Environments
---

### Post by trk on 2007-01-28
Hi,

I installed  ubuntu today on my old Sony VAIO PC. It works very well. However, there is a continuous noise - as though the hard disk or the CD is constantly spinning - I tried opening and closing the CD drive(there is no CD in it). Has anyone experienced this? Any solutions?

Thanks.

---

### Post by 13east on 2007-01-28
i'm getting the same thing on my pavillion zv5000z...

---

### Post by jpkotta on 2007-01-28
The hard drive will constantly spin.  I don't think the default is to spin it down after N seconds.  You can change this behavior with the hdparm command, and make it automatically change when you plug/unplug the AC adapter (if this is a laptop) by editing /etc/acpi/power.sh (example attached).

Look for the -B and -S options:
```
man hdparm
```

---

