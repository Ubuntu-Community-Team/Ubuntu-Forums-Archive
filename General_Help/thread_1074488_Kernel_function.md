---
title: "Kernel function"
date: 2009-02-19
forum: General Help
---

### Post by Lekshmi on 2009-02-19
Can any one tell me how copy-to-user and copy-from-user what does in detail with some examples?????

---

### Post by geraldm on 2009-02-19
The example is in the kernel source file. look in /linux-2.6.28/drivers/usb/usb-skeleton.c
In general, the functions are memory-to-memory copy instructions, from kernel memory space to module memory space. 

Gerald

---

### Post by heindsight on 2009-02-19
copy_from_user copies data from a buffer in user space to a kernel buffer and copy_to_user copies data from a kernel buffer to a buffer in user space.

These are usually used to implement system calls. For example, a user process would call the read system call to read data from a file into a buffer in the process's address space. The system call however, runs in the kernel's address space so it first reads the data into a buffer in kernel space and then copies the data to the buffer in the calling process's address space using copy_to_user.

---

