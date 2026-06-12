---
title: "No puc esborrar un DVD-RW"
date: 2008-10-24
forum: Catalan Team
---

### Post by tanreb20 on 2008-10-24
Hola companys!

Aprofitant que ha sortit ja la RC del intrepid havia pensat agafar un DVD-RW que tenia amb el XUbutnu i fer la prova.

Pero avui quan he intentat esborrarlo no ho ha hagut manera.

Normalment u faig amb el brasero pero avui em diu que no reconeix cap unitat de dades.

Vaig a /media/ i el CD alla esta, is i faig un mount -l em diu aixó:

/dev/scd0 on /media/Xubuntu 8.04.1 i386 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8) [Xubuntu 8.04.1 i386]

He intentat esborrar el DVD desde consola fent:

```
sudo umount /dev/cdrom
 cdrecord dev=/dev/cdrom blank=fast

```
i em retorna aixo:

wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-T20N '
Revision       : 'WT03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 4234 KB/s
Starting to write CD/DVD at speed  24.0 in real BLANK mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 01 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A A1 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
wodim: Cannot blank disk, aborting.
wodim: Some drives do not support all blank types.
wodim: Try again with wodim blank=all.

Que em podrieu ajudar?¿

---

### Post by papapep on 2008-10-24
Llegeix el que et diuen els errors:

> wodim: Cannot blank disk, aborting.
wodim: Some drives do not support all blank types.
wodim: **Try again with wodim blank=all**.


---

### Post by tanreb20 on 2008-10-24
la resposta al blank=all:

wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-T20N '
Revision       : 'WT03'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Speed set to 4234 KB/s
Starting to write CD/DVD at speed  24.0 in real BLANK mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Errno: 5 (Input/output error), blank unit scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A A1 00 00 80 30 05 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.002s timeout 9600s
wodim: Cannot blank disk, aborting.

Em diu que no es un disc en blank.. que ja es la idea!

---

### Post by papapep on 2008-10-24
Aquí jo ja em perdo:

> cannot write medium - incompatible format

Ho has provat amb el K3B?

---

### Post by tanreb20 on 2008-10-24
Si, ho he provat pero no m'el reconeix!

---

