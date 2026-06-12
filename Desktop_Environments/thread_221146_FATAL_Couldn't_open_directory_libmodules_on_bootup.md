---
title: "FATAL: Couldn't open directory /lib/modules on bootup"
date: 2006-07-22
forum: Desktop Environments
---

### Post by varun0 on 2006-07-22
I recompiled my kernel to add ntfs write support, but when I rebooted my machine I got this error - 

WARNING : Couldn't open directory /lib/modules/2.6.15.7-ubuntu1: no such file or directory
FATAL:  Couldn't open directory /lib/modules/2.6.15.7-ubuntu1/modules.dep.temp for writing: no such file or directory

That folder does exist. Modules.dep.temp doesn't. I tried copying modules.dep to modules.dep.temp, but that didn't work either. I've done "make modules" and "make modules_install", too. I have the correct initrd - well I ran makeinitramfs, to give me initrd.img-2.6.15.7-ubuntu1

If anyone has any other suggestions, I would really appreciate it

Thanks!

---

### Post by mlind on 2006-07-22
Ubuntu kernel has ntfs support enabled by default, so you don't need to compile your own kernel.

For Debian based distros like Ubuntu, use kernel-package and **make-kpkg** for the kernel build process.

---

