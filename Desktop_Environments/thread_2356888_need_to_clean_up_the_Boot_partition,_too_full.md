---
title: "need to clean up the /Boot partition, too full"
date: 2017-03-27
forum: Desktop Environments
---

### Post by Heeter on 2017-03-27
Hey all,

I was trying to upgrade to the next kernel, 4.8.0-44, but It keeps failing, I figured that it is because my /boot partition is full. I finally managed to uninstall one kernel (4.4.0-66, I believe) and did install the 4.8.0-44 and make it active.

Can someone tell me how I can remove all the unused kernels that is soaking up all the space on the /boot drive? It currently has 250MB alotted to it, and it is down to around 20MB.

Regards

```

adminpc@adminpc ~ $ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                             Version               Architecture          Description
+++-================================-=====================-=====================-=====================================================================
un  linux-image                      <none>                <none>                (no description available)
un  linux-image-3.0                  <none>                <none>                (no description available)
rc  linux-image-3.19.0-32-generic    3.19.0-32.37~14.04.1  amd64                 Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-21-generic     4.4.0-21.37           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic     4.4.0-64.85           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic     4.4.0-66.87           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-67-generic     4.4.0-67.88           amd64                 Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.8.0-42-generic     4.8.0-42.45~16.04.1   amd64                 Linux kernel image for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-4.8.0-44-generic     4.8.0-44.47~16.04.1   amd64                 Linux kernel image for version 4.8.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-32-gene 3.19.0-32.37~14.04.1  amd64                 Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-gener 4.4.0-21.37           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-gener 4.4.0-64.85           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-gener 4.4.0-66.87           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-67-gener 4.4.0-67.88           amd64                 Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.8.0-42-gener 4.8.0-42.45~16.04.1   amd64                 Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
ii  linux-image-extra-4.8.0-44-gener 4.8.0-44.47~16.04.1   amd64                 Linux kernel extra modules for version 4.8.0 on 64 bit x86 SMP
adminpc@adminpc ~ $ 

```

---

### Post by deadflowr on 2017-03-27
You only have single kernel installed in the dpkg list.
What does 
```
ls /boot
```
show?

---

### Post by Heeter on 2017-03-27
Hi,

```

adminpc@adminpc ~ $ ls /boot
abi-4.8.0-44-generic         lost+found
config-4.8.0-44-generic      memtest86+.bin
extlinux                     memtest86+.elf
grub                         memtest86+_multiboot.bin
initrd.img-4.4.0-66-generic  System.map-4.8.0-44-generic
initrd.img-4.8.0-44-generic  vmlinuz-4.8.0-44-generic
adminpc@adminpc ~ $ 

```

I wonder what is sucking up so much real estate!

Regards

---

### Post by bcschmerker on 2017-03-28
**That's a lot of superseded Kernel packages!**  This task is a lot more straightforward with Synaptic Package Manager, but I'd start with: 
```
sudo apt purge --remove linux-*-3.* linux-*-4.4.0-21-generic linux-*-4.4.0-64-generic linux-*-4.4.0-66-generic linux-*-4.8.0-42-generic
``` 
if Synaptic is unavailable.

---

### Post by Heeter on 2017-03-28
Great, That removed about 200MB, Thanks!!!

---

