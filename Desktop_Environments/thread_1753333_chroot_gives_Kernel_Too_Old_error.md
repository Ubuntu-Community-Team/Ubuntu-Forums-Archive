---
title: "chroot gives Kernel Too Old error"
date: 2011-05-08
forum: Desktop Environments
---

### Post by towheedm on 2011-05-08
I have Fedora 14 installed on my system.  It's mounted at /mnt/fedora.  I'm trying to chroot into it using:
```
sudo chroot /mnt/fedora/
```but I get this error message:
```
FATAL: kernel to old.
```I have the latest Fedora kernel release installed: [COLOR=Blue]vmlinuz-2.6.35.12-90.fc14.i686.[/COLOR]

I also have openSUSE 11.3 using kernel: [COLOR=Blue]vmlinuz-2.6.34.7-0.7-default [/COLOR]and Sabayon using kernel: [COLOR=Blue]kernel-genkernel-x86-2.6.37-sabayon[/COLOR], both of which I can successfully chroot into.

Any idea why I'm getting the error with Fedora 14?

Thanks.

---

