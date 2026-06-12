---
title: "Partitioning motherboard raid"
date: 2009-06-24
forum: General Help
---

### Post by marks256 on 2009-06-24
I have a motherboard with on-board raid. I have it setup with two 1tb drives in raid 1 through the built in raid utility.

I go in to partition it then using gparted, but it still shows up as two separate disks. sdb and sdc. I was under the impression it should show up as one single drive...

What gives? I'm using a live CD to partition the raid, because the installed OS is ubuntu server, and i didn't feel like partitioning through the command line.

---

### Post by marks256 on 2009-06-24
bump

---

### Post by marks256 on 2009-06-24
here is the output of fdisk -l
```
 sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009db79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       29164   234259798+  83  Linux
/dev/sdc2           29165       30401     9936202+   5  Extended
/dev/sdc5           29165       30401     9936171   82  Linux swap / Solaris

```

Why is it detecting sda and sdb as separate drives when they are the drives set in Raid 1? sdc is the boot drive.

Here is the output of dmraid -ay -vv
```
sudo dmraid -ay -vv
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: pdc metadata discovered
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: pdc metadata discovered
NOTICE: /dev/sdb: sil     discovering
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: pdc metadata discovered
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
NOTICE: added /dev/sdc to RAID set "pdc_jgigijbii"
NOTICE: added /dev/sdb to RAID set "pdc_bahbfbgbh"
NOTICE: added /dev/sda to RAID set "pdc_bahbfbgbh"
RAID set "pdc_jgigijbii" was not activated
RAID set "pdc_bahbfbgbh" already active
INFO: Activating mirror raid set "pdc_bahbfbgbh"
NOTICE: discovering partitions on "pdc_bahbfbgbh"
NOTICE: /dev/mapper/pdc_bahbfbgbh: dos     discovering
```

here are some more (hopefully useful) outputs

```
sudo dmraid -r
/dev/sdc: pdc, "pdc_jgigijbii", stripe, ok, 486328064 sectors, data@ 0
/dev/sdb: pdc, "pdc_bahbfbgbh", mirror, ok, 1953124992 sectors, data@ 0
/dev/sda: pdc, "pdc_bahbfbgbh", mirror, ok, 1953124992 sectors, data@ 0

```

```
ls /dev/mapper/
control  pdc_bahbfbgbh

```


So it seems that it is being detected SOMEHWERE, but not where i need it :(

---

### Post by marks256 on 2009-06-24
Ok, I would first like to apologize for my taking up space on the ubuntu forums, but i figured it out on my own.

It turns out pdc_bahbfbgbh in /dev/mapper *_**IS**_* the raid. So all i had to do was boot my live cd, install dmraid on the live cd, type in dmraid -ay -vv to build the raid table (at least i think that is what it does), and then simply check /dev/mapper to make sure it was there, and it was. Then i typed in gparted /dev/mapper/pdc_bahbfbgbh and now it is partitioning my disks :) At least i think so. Both of the status leds on the drives are going together, so i'm assuming it is working :)

Next all i should have to do is reboot to my server install, and mount the drive.

---

### Post by egalvan on 2009-06-24
> **marks256 said:**
> Ok, I would first like to apologize for my taking up space on the ubuntu forums, but i figured it out on my own.

No need to apologize... knowledge is never wasted.

And keep us posted on your progress.

---

### Post by marks256 on 2009-06-24
Ok it worked. Got raid up and working. Now i just need to figure out how to have it mount on boot. That doesn't sound too hard though.

---

