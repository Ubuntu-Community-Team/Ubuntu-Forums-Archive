---
title: "Installing Kubuntu as a guest OS in VMware"
date: 2005-09-22
forum: Desktop Environments
---

### Post by jbinc1 on 2005-09-22
Does anyone know how to install VMware Tools in Kubuntu while running it as a guest OS in VMware Workstation 5?

Thanks in advance.

---

### Post by mlomker on 2005-09-22
[QUOTE=jbinc1]Does anyone know how to install VMware Tools in Kubuntu while running it as a guest OS in VMware Workstation 5?
[/QUOTE]

If you select to install it from the menu it'll put a folder on your desktop (if memory serves).  You then untar the package and do the ./configure, make, make install routine.  You'll need to download your kernel-headers and build-essential for it.

---

### Post by jbinc1 on 2005-09-22
Thanks. I got it working. I was missing the kernel-headers and build-essential part.:grin:

---

