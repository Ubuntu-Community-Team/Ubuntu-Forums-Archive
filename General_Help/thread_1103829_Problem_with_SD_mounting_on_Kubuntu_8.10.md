---
title: "Problem with SD mounting on Kubuntu 8.10"
date: 2009-03-23
forum: General Help
---

### Post by pipposanta on 2009-03-23
Hi,
I have a problem mounting my SD card. When I load the system it appears in the sidebar of Dolphin but it isn't mounted so I have to click on to mount it. I must premise that the memory card is always inserted into the computer and is formatted FAT32. I'm using Kubuntu 8.10 with KDE 4.2.1.

Here are the results of some commands and the content of the fstab

fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f9f9bc64-a11d-46bf-be50-4aed6ff1decf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=f4e3ff4b-3a76-4ac4-9717-4514ff4dd1ea none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

sudo fdisk -l
```
Disco /dev/sda: 7682 MB, 7682605056 byte
255 testine, 63 settori/tracce, 934 cilindri
Unità = cilindri di 16065 * 512 = 8225280 byte
Identificativo disco: 0xb73eb73e

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         887     7124796   83  Linux
/dev/sda2             888         934      377527+   5  Esteso
/dev/sda5             888         934      377496   82  Linux swap / Solaris
```

ls /dev/disk/by-uuid/ -la
```
totale 0
drwxr-xr-x 2 root root 100 2009-03-23 08:21 .
drwxr-xr-x 6 root root 120 2009-03-23 08:21 ..
lrwxrwxrwx 1 root root  15 2009-03-23 08:21 F0F4-1981 -> ../../mmcblk0p1
lrwxrwxrwx 1 root root  10 2009-03-23 08:21 f4e3ff4b-3a76-4ac4-9717-4514ff4dd1ea -> ../../sda5
lrwxrwxrwx 1 root root  10 2009-03-23 08:21 f9f9bc64-a11d-46bf-be50-4aed6ff1decf -> ../../sda1
```

lsmod | grep sdhci
```
sdhci_pci              15360  0
sdhci                  23940  1 sdhci_pci
mmc_core               58268  2 mmc_block,sdhci
```

Any suggestions?

Thanks in advance!

---

### Post by pipposanta on 2009-03-24
up!

---

### Post by pipposanta on 2009-03-24
anyone??

---

