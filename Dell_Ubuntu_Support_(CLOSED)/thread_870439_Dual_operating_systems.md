---
title: "Dual operating systems?"
date: 2008-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tye959 on 2008-07-25
I have a dell vostro 1400 and just recently booted ubuntu 7.10 hardy and in the installation it never asked me to delete windows. But it goes straight to ubuntu login so I thought that I just had ubuntu but do I have both. Is there a key combination? Thanks

---

### Post by ibutho on 2008-07-25
If Windows was installed on this laptop and the Ubuntu Grub does not see it, it could be that you inadvertantly wiped it off by choosing the partitioning option that lets Ubuntu use all the disk space. To check your partitions, run Applications -> Accessories -> Terminal and enter
```
sudo fdisk -l
```
Post back the output.

---

### Post by tye959 on 2008-07-25
uhh I dont really know what this means but this is what it said.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19083   153284166   83  Linux
/dev/sda2           19084       19457     3004155    5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris
matt@matt-laptop:~$

---

### Post by ibutho on 2008-07-25
The outpt shows that there are not Windows partitions on your disk. This means that you could have accidentally deleted your Windows installation.

---

### Post by tye959 on 2008-07-25
Just my luck... thanks for the help :)

---

