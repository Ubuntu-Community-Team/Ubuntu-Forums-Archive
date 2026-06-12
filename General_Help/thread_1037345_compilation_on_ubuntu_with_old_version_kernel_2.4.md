---
title: "compilation on ubuntu with old version kernel 2.4"
date: 2009-01-11
forum: General Help
---

### Post by yuceea on 2009-01-11
Hi everyone. I new at kernel compilation but i have worked on redhat 2.4.20-8 
Now i want to use same kernel version at my new ubuntu 
I have added 2.4.20-8 source code of kernel at the /usr/src of my system. when i have tried to compile with true commands i cannot create any image with make bzImage

first of all i want to know is it possible make compilation on new ubuntu version(which has 2.6 kernel) for 2.4 kernel ?

---

### Post by yuceea on 2009-01-11
is there any idea ?

---

### Post by Yellow Pasque on 2009-01-11
Why would you want to use a 2.4 kernel?

---

### Post by yuceea on 2009-01-12
anyway i achieved to compile 2.4 but i  have some questions again 
How can i add my new image-kernel to grub menu

---

### Post by mgol on 2009-01-12
If You made initrd images, it should look like:

```

title		Ubuntu 8.04.1, kernel __YOUR_KERNEL_VERSION
uuid		__YOUR_BOOT_PARTITION_UUID
kernel		/vmlinuz-__YOUR_KERNEL_VERSION root=UUID=__YOUR_ROOT_PARTITION_UUID
initrd		/initrd.img-__YOUR_KERNEL_VERSION

```

or, if You don't use UUIDs

```

title		Ubuntu 8.04.1, kernel __YOUR_KERNEL_VERSION
root		/dev/sd__YOUR_BOOT_PARTITION_NUMBER
kernel		/vmlinuz-__YOUR_KERNEL_VERSION root=/dev/sd__YOUR_ROOT_PARTITION_NUMBER
initrd		/initrd.img-__YOUR_KERNEL_VERSION

```

Remember also to put all these *OUTSIDE* of menu.lst part from:
```
### BEGIN AUTOMAGIC KERNELS LIST
```
to:
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```

Otherwise Your entries will be replaced during next kernel update.


Let me just ask - why do You need 2.4 kernel version? They're uneffective, they do not use hardware so good as 2.6 kernels; if You don't really need a kernel for some unusual purposes, 2.6 kernel should serve well.

---

### Post by yuceea on 2009-01-12
thanks for quick post i will try tomorrow it

---

