---
title: "My kernel modules do not load at start..."
date: 2009-01-12
forum: General Help
---

### Post by Crafty Kisses on 2009-01-12
So I've compiled the **2.6.28 **kernel for the simple fact that some of my devices didn't work properly, the kernel compile went fairly well, no error messages, but it turns out the kernel modules are not loading at start, so I ran the following:
```
lsmod
```
It only returned the following:
```
Module                  Size  Used by
```
I've obviously already unzipped the tar archive, then I move into the directory I want:
```
ln -s /usr/src/linux-2.6.28 /usr/src/linux
```
Once I've done that I run the following:
```
make menuconfig
```
Once I do that, I want to make the modules, so I run this:
```
make && make modules_install
```
The module I'm looking for doesn't appear when I run the following:
```
modprobe ath5k
```
Then I was thinking to myself, I could have messed up, maybe I didn't install the kernel image, so I did the following:
```
make menuconfig
make
cp arch/x86/boot/bzImage /boot/vmlinuz-2.6.xx
cp System.map /boot/System.map-2.6.xx
make modules_install
```
So I did that, then I ran the following again:
```
make modules_install
```
It came back as the following:
```
INSTALL arch/x86/kernel/test_nx.ko
  INSTALL drivers/net/wireless/ath9k/ath9k.ko
  INSTALL drivers/scsi/scsi_wait_scan.ko
  DEPMOD  2.6.27.10
```
There's obviously something wrong, so if anyone can give me any information or anything else I can try, I know this is kind of complicated situation, but I'm pretty stumped on this one.

---

