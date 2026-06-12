---
title: "XEN installation - lilo error"
date: 2006-02-17
forum: Desktop Environments
---

### Post by MrCheese on 2006-02-17
Hi, I want to get to grips with Xen the easy way with the Xen binary tarball. The problem starts after running the install script. For various reasons I run lilo instead of grub. Running lilo to install the new Xen kernel into the boot scheme, I get an error "kernel setup string is too long. New kernel will overwrite boot sector".

I'm trying to use the 2.6.12-6-Xen0 kernel as per docs.

---

### Post by heimo on 2006-02-17
AFAIK, lilo can't be used to boot Xen. :neutral:

---

### Post by MrCheese on 2006-02-17
D'oh!!

---

### Post by waster on 2006-02-20
Here's my grub stanza:

title   Xen3.0
root    (hd0,0)
kernel /xen.gz
module /vmlinuz-2.6.12-xen root=/dev/mapper/Ubuntu-root ro console=tty0
module /initrd-2.6.12-xen.img
boot

see my wiki entry:
[https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuBreezy](https://wiki.ubuntu.com/XenVirtualMachine/XenOnUbuntuBreezy)

---

