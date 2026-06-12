---
title: "c header files ?"
date: 2006-06-20
forum: Desktop Environments
---

### Post by petervdv on 2006-06-20
hi,
I am trying to install vmware (on dapper)
where can I find the c header files? the wizzard is asking me this question

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include]

---

### Post by petervdv on 2006-06-20
sudo apt-get install kernel-headers
Reading package lists... Done
Building dependency tree... Done
Package kernel-headers is a virtual package provided by:
  kernel-headers-2.4.27-2-k7-smp 2.4.27-12
  kernel-headers-2.4.27-2-k7 2.4.27-12
  kernel-headers-2.4.27-2-k6 2.4.27-12
  kernel-headers-2.4.27-2-686-smp 2.4.27-12
  kernel-headers-2.4.27-2-686 2.4.27-12
  kernel-headers-2.4.27-2-586tsc 2.4.27-12
  kernel-headers-2.4.27-2-386 2.4.27-12
  kernel-headers-2.4.27-2 2.4.27-12
You should explicitly select one to install.
E: Package kernel-headers has no installation candidate


btw: I am running  2.6.15-25-386

---

### Post by Ramses de Norre on 2006-06-20
```
sudo aptitude install kernel-headers-`uname -r`
```

---

### Post by petervdv on 2006-06-20
sudo aptitude install kernel-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kernel-headers-2.6.15-25-386"

---

### Post by Ramses de Norre on 2006-06-20
Ow.. well I see I've got ```
ii  linux-headers-2.6.12-10                2.6.12-10.32                          Header files related to Linux kernel version
ii  linux-headers-2.6.12-10-k7             2.6.12-10.32                          Linux kernel headers 2.6.12 on AMD K7
ii  linux-headers-2.6.15-23                2.6.15-23.39                          Header files related to Linux kernel version
ii  linux-headers-2.6.15-23-k7             2.6.15-23.39                          Linux kernel headers 2.6.15 on AMD K7 SMP/UP
ii  linux-headers-2.6.15-25                2.6.15-25.43                          Header files related to Linux kernel version
ii  linux-headers-2.6.15-25-k7             2.6.15-25.43                          Linux kernel headers 2.6.15 on AMD K7 SMP/UP
ii  linux-kernel-headers                   2.6.11.2-0ubuntu18                    Linux Kernel Headers for development

```
I don't know which one is needed but vmware works here, I'd say try them ;)

---

### Post by petervdv on 2006-06-20
yes thank you!
linux-headers-2.6.15-25 did the trick

---

