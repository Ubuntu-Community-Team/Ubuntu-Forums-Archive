---
title: "problem with mount with fstab"
date: 2009-04-12
forum: General Help
---

### Post by davidtuti on 2009-04-12
Hi,

I have kubuntu 8.1. I have an external hard drive with a ext3 partition, and I'm tying to mount the partition at boot.

I put in the fstab:


...
...
...
/dev/sdc2       /descargas  ext3   defaults,rw,user,noauto 0 


But it doesn't works! 
Any help?
Thanks and sorry for my english!

---

### Post by unutbu on 2009-04-12
Each valid line in /etc/fstab (besides comments) must have 6 space-separated fields. The line you posted only has 5 fields. Try
```

/dev/sdc2 /descargas ext3 defaults,user,noauto 0  2
```

PS. "defaults" means "rw,suid,dev,exec,auto,nouser,async".
So there is no need to write "defaults,rw".

---

### Post by kpatz on 2009-04-12
Also, "noauto" means to *not* mount the drive automatically on boot.  So if you want it to mount automatically, use "auto".

---

### Post by davidtuti on 2009-04-12
> **kpatz said:**
> Also, "noauto" means to *not* mount the drive automatically on boot.  So if you want it to mount automatically, use "auto".

Many thaks! I thought that if I write in the fstab, automatically mount the drive on boot and therefore there is no option to mount automatically in fstab.

Thanks a lot!

---

