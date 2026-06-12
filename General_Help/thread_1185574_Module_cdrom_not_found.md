---
title: "Module cdrom not found"
date: 2009-06-12
forum: General Help
---

### Post by roxy2 on 2009-06-12
Hi,

I cannot mount my cdrom in Ubuntu 9.04.

I am running the following kernel:
```
uname -a
Linux amd-quad 2.6.28-13-generic #44-Ubuntu SMP Tue Jun 2 07:55:09 UTC 2009 x86_64 GNU/Linux
```
and I see there is no cdrom directory in /lib/modules/2.6.28-13-generic/kernel/drivers/

Thus I cannot modprobe the cdrom module:
```
modprobe cdrom
FATAL: Module cdrom not found.
```

I did not remove any packages in Ubuntu.
What is wrong; is there a bug in 2.6.28-13?

---

### Post by kevinlyfellow on 2009-06-12
In ubuntu the cdrom drivers are built into the kernel and not as modules.

If you are having issues, it looks like you aren't the only one.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357148]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357148")

---

### Post by roxy2 on 2009-06-12
> **kevinlyfellow said:**
> In ubuntu the cdrom drivers are built into the kernel and not as modules.

If you are having issues, it looks like you aren't the only one.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357148]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/357148")

Thanks. So it is a bug?

---

### Post by kevinlyfellow on 2009-06-12
I'm not entirely sure.  If you have a cdrom drive and it's not working properly, you have a bug.  But the missing module is not, it's just that the kernel team decided to build the driver directly into the kernel instead of having the driver as a module.  This means that whenever the kernel is loaded, the driver should be in it.  If it were a module, the kernel would load and then the module inserted at a later time.

---

### Post by roxy2 on 2009-06-14
OK,

I have looked inside my computer and there was no SATA cable connected to my CD-ROM.

Sorry
Thank for help, anyway.

---

### Post by kevinlyfellow on 2009-06-14
:-b

---

