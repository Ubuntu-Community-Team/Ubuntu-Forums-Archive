---
title: "lvm2 and custom kernel"
date: 2006-01-05
forum: Desktop Environments
---

### Post by hone on 2006-01-05
Hello,

I'm trying to compile a custom kernel, but I can't seem to get it to boot up.  I think I'm missing some configurations on my kernel.  It won't mount my lvm partitions on boot up.  I need them to complete the startup of the system.  The preconfigured kernels from apt work, but I'm not sure why mine don't.  I've enabled device map support and lvm/raid support both are built into the kernel.  I have cramfs, ext2 (/boot), ext3 (/) built in.  I did a make-kpkg clean && make-kpkg --initrd kernel_image and then dpkg -i *.deb for he kernel image.  Yeah, so if any light could be given, I'd greatly appreciate it, since I need to mak e a custom kernel to compile my onboard nic card for my asrock uli board.

---

