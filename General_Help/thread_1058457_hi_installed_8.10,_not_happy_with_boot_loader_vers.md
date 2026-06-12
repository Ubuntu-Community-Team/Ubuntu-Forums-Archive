---
title: "hi installed 8.10, not happy with boot loader versons"
date: 2009-02-02
forum: General Help
---

### Post by Swi on 2009-02-02
Hi,

boot loader is showing 3 versions 2.6.27-11/7/9

I want to keep the latest kernel verson only.How can I do that.

below is the list from boot dir.

pradeep@pradeep:/boot$ ls
abi-2.6.27-11-generic         memtest86+.bin
abi-2.6.27-7-generic          System.map-2.6.27-11-generic
abi-2.6.27-9-generic          System.map-2.6.27-7-generic
config-2.6.27-11-generic      System.map-2.6.27-9-generic
config-2.6.27-7-generic       vmcoreinfo-2.6.27-11-generic
config-2.6.27-9-generic       vmcoreinfo-2.6.27-7-generic
grub                          vmcoreinfo-2.6.27-9-generic
initrd.img-2.6.27-11-generic  vmlinuz-2.6.27-11-generic
initrd.img-2.6.27-7-generic   vmlinuz-2.6.27-7-generic
initrd.img-2.6.27-9-generic   vmlinuz-2.6.27-9-generic
pradeep@pradeep:/boot$

---

### Post by mikewhatever on 2009-02-03
Open synaptic package manager and remove 'linux-image-2.6.27-9-generic' and 'linux-image-2.6.27-7-generic'. The boot loader menu should get update in the process.

---

### Post by Swi on 2009-02-03
thank you

---

