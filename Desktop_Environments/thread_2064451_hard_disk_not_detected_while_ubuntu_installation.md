---
title: "hard disk not detected while ubuntu installation"
date: 2012-09-29
forum: Desktop Environments
---

### Post by justonemoretime on 2012-09-29
Hi all
 i want to install ubuntu in fujitsu celcius r670(workstaion)
while installation hard disk is not detected, tried bios settings didnt work out please help me on this.

---

### Post by oldfred on 2012-09-29
Welcome to the forums.

Is there something special about this system? Does BIOS report drive correctly. Is it a standard PC or server type with RAID? Or UEFI?

Does liveCD or USB boot?

If you can boot liveCD post this:

sudo fdisk -lu
or 
sudo parted - l

---

### Post by gordintoronto on 2012-09-29
Google turned this up, perhaps it will help you:
"What finally worked was removing the drive from the SAS port and connecting to the SATA port. Everything installed smoothly after that."

---

