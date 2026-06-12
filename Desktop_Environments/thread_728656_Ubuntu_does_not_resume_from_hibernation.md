---
title: "Ubuntu does not resume from hibernation"
date: 2008-03-19
forum: Desktop Environments
---

### Post by ubuntoexpert on 2008-03-19
My Ubuntu 7.04 seems to enter into hibernation nicely but does not resume from it. When I try to boot it after having run hibernation, I get a black screen. Only way to make system boot is to add the 'noresume' command to the kernel boot line in GRUB. Any ideas?

---

### Post by mali2297 on 2008-03-19
How far do you get? Remove *quite* and *splash* from the kernel boot line to see what's happening.

Check that you have swap enabled,
```

free -m

```

Also, check
```

sudo fdisk -l | grep swap
cat /etc/initramfs-tools/conf.d/resume

```
so that RESUME is set to the swap partition.

---

