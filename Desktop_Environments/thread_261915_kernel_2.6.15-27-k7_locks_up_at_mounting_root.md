---
title: "kernel 2.6.15-27-k7 locks up at mounting root"
date: 2006-09-20
forum: Desktop Environments
---

### Post by chadk on 2006-09-20
When trying to boot into the new kernel 2.6.15-27-k7 that I just updated to (using the system updater) it gets to the second line and locks up at "Mounting root filesystem"
kernel 2.6.15-26-k7 is still working fine.
The grub lines look identical.
```

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot
```
Of course the 27 lines have 27 not 26 but other than that, the same.

---

