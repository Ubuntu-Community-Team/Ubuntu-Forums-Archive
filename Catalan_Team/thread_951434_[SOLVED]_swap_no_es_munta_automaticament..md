---
title: "[SOLVED] swap no es munta automaticament."
date: 2008-10-18
forum: Catalan Team
---

### Post by indiosincracia on 2008-10-18
tinc gutsy 7.10
particions:
indiosincracia@tontet:~$ sudo fdisk -l /dev/sd*
[sudo] password for indiosincracia:

Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001cda2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris

Disk /dev/sda1: 19.1 GB, 19123743744 bytes
255 heads, 63 sectors/track, 2324 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda1 doesn't contain a valid partition table

Disk /dev/sda5: 880 MB, 880072704 bytes
255 heads, 63 sectors/track, 106 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda5 doesn't contain a valid partition table


quan inicio l'ordinador l'espai d'intercanvi no està activat, ho he de fer manualment:
sudo swapon /dev/sda5

amb CD Live volia saber si hi ha algun error de disc:
sudo e2fsck -y -f -v /dev/sda5
Couldn't find ext2 superblock, trying backup blocks...
e2fsck:Bad magic number in superblock while truing to open /dev/sda5
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you may running e2fsck with an alternative superblock.

(and not swap or something else) diu, com puc saber si hi ha errors a wap doncs,
i com es pot montar automaticament al iniciar la ferralla, gràcies de nou. 

/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=17b2670b-aa3f-4509-b1a8-6f5c85a13941 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=bf0812e4-7dcc-4cb6-bc24-868b44ab514c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by CarlesOriol on 2008-10-18
Prova de fer un 

sudo vol_id /dev/sda5

i comprova que el ID_FS_UUID= sigui igual al # /dev/sda5 UUID=bf0812e4-7dcc-4cb6-bc24-868b44ab514c 

Si és això modifica el fstab amb el nombre nou.

---

### Post by indiosincracia on 2008-10-18
indiosincracia@tontet:~$ sudo vol_id /dev/sda5
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
indiosincracia@tontet:~$

no m'hi surt res aquí ID_FS_UUID=

---

### Post by CarlesOriol on 2008-10-18
llavors canvia la linia del fstab:

de

# /dev/sda5
UUID=bf0812e4-7dcc-4cb6-bc24-868b44ab514c none swap sw 0 0

a

/dev/sda5  none swap sw 0 0

---

### Post by indiosincracia on 2008-10-18
Justa la fusta, ja tira això.
Merci.

---

