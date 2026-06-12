---
title: "Nvidia  nforce on UBUNTU"
date: 2006-08-24
forum: Desktop Environments
---

### Post by goamind on 2006-08-24
Greetings!
I have installed Ubuntu 6.06 on my new Asus MB based on Northbridge Geforce 6150 GPU and SOuthbridge:nforce 430MCP. I have an install CD with linux drivers but they are not suited for Ubuntu! When I ran it, I got this error: RROR: Unable to find the system utility `ld`; please make sure you have
the package 'binutils' installed. If you do have binutils installed,
then please check that `objcopy` is in your PATH.
I found the ld file as ld_static, renamed it to ld, and installation passed this problem, but then I got the error:
RROR: Unable to find the system utility `objcopy`; please make sure you have
the package 'binutils' installed. If you do have binutils installed,
then please check that `objcopy` is in your PATH.
and I stopped here not knowing what to do next.
I really need to install these drivers so please help me out with this.
Thanks a lot!

---

### Post by vangheem on 2006-08-24
Try installing compilers first.

Open up the terminal and type.

```
sudo apt-get install build-essential
```

---

### Post by goamind on 2006-08-24
thanks!!! it worked, but I am facing the next problem:
ERROR: Unable to find the kernel source tree for the currently running
kernel. Please make sure you have installed the kernel source files
for your kernel; on Red Hat Linux systems, for example, be sure you
have the 'kernel-source' rpm installed. If you know the correct
kernel source files are installed, you may specify the kernel source
path with the '--kernel-source-path' commandline option.

OK


I installed some kernel sources from synaptic (but if I remember well, they were kinda old, not 2.6... kernel) but I can't find the sourcepath

And more: for the Display driver, I need to run it outside X, but I do not know how to do that.
Tks for all the udnerstanding!

---

### Post by peabody on 2006-08-24
> **goamind said:**
> thanks!!! it worked, but I am facing the next problem:
ERROR: Unable to find the kernel source tree for the currently running
kernel. Please make sure you have installed the kernel source files
for your kernel; on Red Hat Linux systems, for example, be sure you
have the 'kernel-source' rpm installed. If you know the correct
kernel source files are installed, you may specify the kernel source
path with the '--kernel-source-path' commandline option.

OK


I installed some kernel sources from synaptic (but if I remember well, they were kinda old, not 2.6... kernel) but I can't find the sourcepath

And more: for the Display driver, I need to run it outside X, but I do not know how to do that.
Tks for all the udnerstanding!

I think what you want is the kernel-headers package.

---

