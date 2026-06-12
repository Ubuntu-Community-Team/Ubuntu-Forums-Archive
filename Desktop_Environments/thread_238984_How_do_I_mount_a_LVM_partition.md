---
title: "How do I mount a LVM partition"
date: 2006-08-18
forum: Desktop Environments
---

### Post by jsmidt on 2006-08-18
I have a dual boot with ubuntu and debian.  I really messed my debian partition up and will need to reinstall it.  When in Ubuntu I want to mount my Debian Partition.  It is /dev/sda6.  The problem is it is a LVM partition, and somehow keeps /home, /usr separate.  Does anybody know how to mount this partition?  What filesystem do I need to use?  Thanks

---

### Post by jsmidt on 2006-08-18
I figured it out.  LVM partions look like they were stored under /dev/mapper so 
```

sudo mount -t ext3 /dev/mapper/Debian-home /mnt/debian

```


worked. :)

---

