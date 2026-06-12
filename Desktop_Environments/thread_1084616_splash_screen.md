---
title: "splash screen"
date: 2009-03-02
forum: Desktop Environments
---

### Post by qbox on 2009-03-02
Hi
Maybe this is wrong category for this. If it is move to the right category.

Ubuntu 8.04
When system boot I didnt see splash screen. (The ubuntu logo and loading line) I see the text while building. In menu.lst I have this.

```
## ## End Default Options ##
title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic-STABLE
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro quiet splash vga=791
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-20-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-20-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro single
initrd		/boot/initrd.img-2.6.24-20-generic

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-18-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-18-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro single
initrd		/boot/initrd.img-2.6.24-18-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=543a25fe-e0bb-4453-be57-994e9a342a65 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin

title 		Windows XP
root 		(hd0,0)
makeactive
chainloader +1

### END DEBIAN AUTOMAGIC KERNELS LIST
```
Everything looks fine. On Login out I see the splash screen.
Any help?

---

