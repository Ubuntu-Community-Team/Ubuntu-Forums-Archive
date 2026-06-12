---
title: "No booting after installing ubuntu"
date: 2010-07-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Joe9 on 2010-07-29
I installed ubuntu on dell inspiron 15R laptop and once I booted win 7 and restarted I get a error message no boot media found Please tell me a way to uninstall ubuntu ?

---

### Post by Joe9 on 2010-07-30
Hello, I installed ubuntu 10.04 on my laptop accn to the first option it  tells install alongside other os I can boot in ubuntu but when I load  windows 7 and the restart it I get a error message no boot media  available please tell me a method to remove the ubuntu and use only win 7

---

### Post by ugm6hr on 2010-07-31
After booting Ubuntu, please type the following into Terminal and give output here:
```
sudo fdisk -l
```

This lists all the partitions on the HD, so we can see whether a W7 partition still remains.

If it does, the possibilities are that the bootloader (Grub 2) points to the wrong place, or that the W7 partition has become corrupted.

I'm no expert at resolving either of these issues, but, hopefully, someone will be able to help once you've given the above detail.

---

