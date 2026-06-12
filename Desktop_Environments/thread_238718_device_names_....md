---
title: "device names ..."
date: 2006-08-18
forum: Desktop Environments
---

### Post by Iarwain ben-adar on 2006-08-18
Hi,
I recently deleted a partition on my hard drive. Now, when i want to start Ubuntu, the pc keeps looking for /dev/hdc9 but because of the partition delete (was /dev/hdc4), hdc9 now is called hdc8...

Anyone knows how to either change the device name (hdc8 => hdc9) OR make Ubuntu know that hdc9 is now called hdc8 ?


Iarwain

---

### Post by givré on 2006-08-18
You probably want to change your /etc/fstab.
Also, to know which partition is what, check sudo fdisk -l

---

### Post by Iarwain ben-adar on 2006-08-18
Thanks a lot =)

Pc is working a-ok now :D


Iarwain

---

