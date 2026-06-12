---
title: "Problems using grub-gfxboot 0.97-42 &amp; Ext4 FS"
date: 2009-06-14
forum: General Help
---

### Post by KDarkSigma on 2009-06-14
Hello all... ^^
I have a problem, or something like that with grub-gfxboot package over ubuntu 9.04, i hope somebody can help with this...

OK, first the background...

This is my partitions table:

```
--------------------------------------------------------------------------------
System: Ubuntu 9.04 (2.6.28-11-generic i686) 32bits

Disco /dev/sda: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x97d48653

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1         638     5124703+   b  W95 FAT32
/dev/sda2             639        4463    30724312+  bf  Solaris
/dev/sda3            4464       24321   159509385    f  W95 Ext'd (LBA)
/dev/sda5            4464        9563    40965718+   7  HPFS/NTFS
/dev/sda6            9564       14663    40965718+   7  HPFS/NTFS
/dev/sda7           14664       19763    40965718+  83  Linux
/dev/sda8           19764       23588    30724281   83  Linux
/dev/sda9           23589       24321     5887791   82  Linux swap / Solaris

Disco /dev/sdb: 200.0 GB, 200049647616 bytes
255 cabezas, 63 sectores/pista, 24321 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x8f8004b1

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        5100    40965718+  af  Desconocido
/dev/sdb2            5101       10200    40965750   83  Linux
/dev/sdb3           10201       15300    40965750   83  Linux
/dev/sdb4           15301       24321    72461182+   5  Extendida
/dev/sdb5           15301       21675    51207156    b  W95 FAT32
/dev/sdb6           21676       24321    21253963+   b  W95 FAT32

Disco /dev/sdc: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x9d689d68

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1        2550    20482843+  83  Linux
/dev/sdc2            2551        5100    20482875   83  Linux
/dev/sdc3            5101        7650    20482875   83  Linux
/dev/sdc4            7651       19457    94839727+   f  W95 Ext'd (LBA)
/dev/sdc5            7651       10200    20482843+  83  Linux
/dev/sdc6           10201       12113    15366141    b  W95 FAT32
/dev/sdc7           12114       12751     5124703+   b  W95 FAT32
/dev/sdc8           12752       19457    53865913+   b  W95 FAT32
--------------------------------------------------------------------------------
```

My Ubuntu 9.04 is installed on /dev/sda7 using an ext4 FS, and grub (default of this ubuntu version) was installed on MBR with its root on /dev/sda7...

I wish use grub-gfxboot instead of grub, for load the system. Then i downloaded and installed the grub-gfxboot 0.97-11 (removing previously grub using apt-get), but the problem with this version was that, this version don't understand the ext4 FS... Browsing a few minutes over internet, i found a version with ext4 support (grub-gfxboot 0.97-42), and i installed it on MBR with its root on /dev/sda7

This version has boot without problems, but... don't display the graphic menu (message.*)... maybe, i think gfxboot isn't reading the ext4 partition... But this is impossible because in that case, it couldn't found the stage1 or stage2...

I tried to moving the message.* to /dev/sda1 (FAT32 FS) and set in menu.lst:

gfxmenu (hd0,0)/boot/grub/message.*

but the result is the same... it boot without problems but don't display the graph menu...

At the past months, using ubuntu 8.10 with reiser FS and grub-gfxboot 0.97.11, i could boot, showing a graphic menu...

in the others partition, i have installed others systems, with theirs boot loaders respectively. is for that, i need a special boot loaders distribution:

GRUB 1: root (hd0,0) - setup (hd0) - MASTER GRUB
GRUB 2: root (hd0,6) - setup (hd0,6) - Ubuntu Grub
GRUB x: root (other linux partition) - setup (other linux partition)

But, i really want use grub-gfxboot on Ubuntu 9.04 (Ext4) partition...

Can somebody help me with this please ?

P.D.

Please You sorry me for Tarzan English :P

---

### Post by diegogto on 2009-06-28
I had a lot of trouble with gfxboot, i was almost giving up when i found that grub-gfxboot 0.97.**11** doesn't support ext4 and appeared version 0.97.42... Sadly, there are a few message.XXXX out there built for that version, almost all are made for 0.97.11.

All we have to do is to "make" our own message files built for 42. This can be done installing gfxboot package on synaptics or

```
$ sudo apt-get install gfxboot
```

There are also some themes to be built downloadable throw synaptics.

at this post [http://ubuntuforums.org/showpost.php?p=7325554&postcount=733](http://ubuntuforums.org/showpost.php?p=7325554&postcount=733) you can find information about "making" themes. I'm trying to find where to "update" themes (get an old theme and rebuilt it to a new theme supported by the new version of gfx)

any help?

---

