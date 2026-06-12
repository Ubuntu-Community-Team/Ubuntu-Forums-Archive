---
title: "Dpkg'd new kernel - Messed up GRUB"
date: 2005-11-28
forum: Desktop Environments
---

### Post by vtechstu on 2005-11-28
Ok, so I had a driver i needed rolled into my kernel, so when it was done i dpk'd it.  Its the new 2.6.14 kernel.

On reboot, i get an error, something in the new kernel messed up my GRUB loader .  I think its looking in the wrong location for root or something.  Here is the message on safe boot.
```

ACPI: (supports S0 S1 S3 S4 S5 ) <--last good line
VFS: Cannot open root device "sda2" oor unknown-block(0,0)
Please append a correct "root=" boot option
Kernel panic -  not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```


EDIT:  I searched and found that  I needed a certain file.  I booted from a live CD but dont know how to complete this.  Thanks.


mkdir /lib/modules/"the kernel you run"
cp -a /lib/modules/"the kernel you run"/kernel/security/capability.ko /lib/modules/"the kernel you run"boot/
mkinitrd -o /boot/initrd.img-"the kernel you run" "the kernel you run"


Please help. Thanks

---

