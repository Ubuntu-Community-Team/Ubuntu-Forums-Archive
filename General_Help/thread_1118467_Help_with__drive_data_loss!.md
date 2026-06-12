---
title: "Help with  drive data loss!"
date: 2009-04-07
forum: General Help
---

### Post by Takmadeus on 2009-04-07
Greetings.

Today I am in need of desperate help.

Some days ago I made a backup of some sensitive information in my computer, I just copied my home folder in an USB drive.

But today, when I was going to restore it in a new computer, the files are not shown up, when I see the properties of the drive I see that 3.3 Gb are bo}eing used and only 456 are free (my usb drive has 4Gb)

but the previous files do show up normally (the ones that were in there even before I did the backup). When I select all files I see that they weight 464.8 Mb in total.

I am sure that my backup is lying in the 2.83 Gb remaining.

Now, the files are not hidden, even when I select "view hidden", they are not seen.

This case is seen both in windows and linux, so I am sure it is specific for the usb drive.

It is a Markvision 4Gb USB flash drive.

What can I do to rescue that information?

Thanks in advance, any kind of help is welcome :)

---

### Post by hyper_ch on 2009-04-07
plug it in, run

```

sudo fdisk -l

```
and also
```

df -h

```

and post the output here

---

### Post by Takmadeus on 2009-04-07
OK, here it goes:

```
takmadeus@takmadeus-desktop:~$ sudo fdisk -l

Disco /dev/sda: 320.0 GB, 320072933376 bytes
255 cabezas, 63 sectores/pista, 38913 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x2bd2c32a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       12748   102398278+   7  HPFS/NTFS
/dev/sda2           12749       38670   208218465   83  Linux
/dev/sda3           38671       38913     1951897+  82  Linux swap / Solaris

Disco /dev/sdb: 4089 MB, 4089446400 bytes
255 cabezas, 63 sectores/pista, 497 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x0007f336

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1         497     3992121    b  W95 FAT32

Disco /dev/sdf: 4043 MB, 4043308544 bytes
225 cabezas, 32 sectores/pista, 1096 cilindros
Unidades = cilindros de 7200 * 512 = 3686400 bytes
Identificador de disco: 0x0d0c0b0a

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdf1   *           1        1097     3948527+   b  W95 FAT32

Disco /dev/sdg: 4043 MB, 4043308544 bytes
255 cabezas, 63 sectores/pista, 491 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x91f72d24

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdg1   *           1         492     3948512    b  W95 FAT32
La partición 1 tiene distintos finales físicos/lógicos:
     físicos=(490, 254, 63) lógicos=(491, 145, 37)

```

and the output of df -h

```
takmadeus@takmadeus-desktop:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda2             196G  9,4G  177G   6% /
tmpfs                1000M     0 1000M   0% /lib/init/rw
varrun               1000M  112K 1000M   1% /var/run
varlock              1000M     0 1000M   0% /var/lock
udev                 1000M  2,9M  997M   1% /dev
tmpfs                1000M  104K 1000M   1% /dev/shm
lrm                  1000M  2,4M  998M   1% /lib/modules/2.6.27-14-generic/volatile
/dev/scd0             3,9G  3,9G     0 100% /media/cdrom0
/dev/sdb1             3,8G  4,0K  3,8G   1% /media/JUAN E
/dev/sdf1             3,8G  3,4G  457M  89% /media/TAKMADEUS
/dev/sdg1             3,8G   27M  3,8G   1% /media/MHGAITAN 4G

```

As expected, /dev/sdf1 (/media/TAKMADEUS) is the one giving me trouble...

now, what do I do?, is there a tool in linux or windows that allows me to recover this data?

---

### Post by hyper_ch on 2009-04-07
and which drive is the one in question?

---

### Post by dacorr on 2009-04-07
maybe a silly question but did you confirm that the files were copied to the USB pen and that it was unmounted ?

the solution is a simple one,

from a windows machine install FTK imager (forensic tool, free)

install and run

add a device selecting your USB pen

it will say somthing about not detecting a write blocker

then view the structure to see if the folder exists, hopefully the data is only flagged as deleted and has not been overwritten.

---

### Post by Takmadeus on 2009-04-07
> and which drive is the one in question?

as I said before, it is /media/TAKMADEUS (/dev/sdf1)

BTW, where can I get FTK imager?, I cannot find it on google (just reviews and nothing more)

EDIT: OK, did a simple virus scan in windows (with clamwin) and guess what, a lot of CHK files in a FOUND.000 folder appeared. suppose it was just a faulty partition. fortunately linux is good at guessing content from files, so I managed to rescue the important stuff ;)

---

