---
title: "Kernel will not boot - won't load module?"
date: 2009-03-31
forum: General Help
---

### Post by scoobyd00 on 2009-03-31
Hello,

I am trying to get support for my RAID card working (Areca 1100).

I have recompiled my kernel and told it to include the ARCMSR driver using:

```
CONFIG_SCSI_ARCMSR=y
```

It seems it did not compile this into the kernel.

It did compile a kernel module however.

So, I made sure "arcmsr" was in:

```
/etc/initramfs-tools/modules
```

And did:

```
update-initramfs -k all -u
```

When I reboot I get:
```
[   60.664241] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

And there is no mention of my RAID card being detected.

I have unpacked the initrd.img file and looked inside and can see it contains:
```
./lib/modules/2.6.24-23-openvz/kernel/drivers/scsi/arcmsr/arcmsr.ko
```

Can anybody help me understand why my RAID card is not being detected? 

Why is the module not being loaded during the boot process?

Why did CONFIG_SCSI_ARCMSR=y not statically compile the driver?

---

### Post by scoobyd00 on 2009-03-31
OK - it appears there was no "initrd" line inside my grub configuration. Problem solved!

---

