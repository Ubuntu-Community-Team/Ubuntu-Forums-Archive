---
title: "K3B- Error d'escriptura, [no graba]"
date: 2008-06-14
forum: Catalan Team
---

### Post by prostata on 2008-06-14
Des que vaig canviar a hardy tant k3b com brasero em donen problemes, es dir no escriuen.
Poso un DVD verge obro k3b, indico modo multissesion, velocitat auto. mod. de gravació. auto, sistema d'arxius linux/unix+windows, es dir tot el que prenc per defecte el programa, com sempre.

indico els arxius que vull copiar i comença el proces tìpic de k3b per escriure, desprè d'uns moments, buida la caché, actualitza RMA i diu: Error d'escriptura.

He probat amb més "vairetats" però ja he gastat un munt de DVD's. us adjunto el "depurat" per si sabeu més que jo, que segur i podeu donar un cop de má. Gràcies



--"System
-----------------------
K3b Version: 1.0.4

KDE Version: 3.5.9
QT Version:  3.3.8b
Kernel:      2.6.24-18-generic
Devices
-----------------------
HL-DT-ST DVDRAM GSA-4165B DL03 (/dev/scd0, ) [CD-R, CD-RW, CD-ROM, DVD-ROM, DVD-R, DVD-RW, DVD-R DL, DVD+R, DVD+RW, DVD+R DL] [DVD-ROM, DVD-R secuencial, DVD-R Doble capa secuencial, DVD-R doble capa salteado, DVD-RAM, DVD-RW sobreescritura restringida, DVD-RW secuencial, DVD+RW, DVD+R, DVD+R doble capa, CD-ROM, CD-R, CD-RW] [SAO, TAO, En bruto, SAO/R96P, SAO/R96R, RAW/R16, RAW/R96P, RAW/R96R, Sobrescritura restringida]

Burned media
-----------------------
DVD-R secuencial

K3bIsoImager
-----------------------
mkisofs print size result: 282889 (579356672 bytes)
Pipe throughput: 47328000 bytes read, 47323648 bytes written.

Used versions
-----------------------
mkisofs: 1.1.6
growisofs: 7.0.1

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/scd0 obs=32k seek=0'
:-? Failed to change write speed: 22161->22160
/dev/scd0: "Current Write Speed" is 16.4x1352KBps.
          0/579356672 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
    5210112/579356672 ( 0.9%) @1.1x, remaining 18:21 RBU 100.0% UBU   2.9%
    7438336/579356672 ( 1.3%) @0.5x, remaining 16:39 RBU 100.0% UBU 100.0%
   12517376/579356672 ( 2.2%) @1.1x, remaining 12:49 RBU 100.0% UBU 100.0%
:-[ WRITE@LBA=1a30h failed with SK=4h/ASC=09h/ACQ=01h]: Input/output error
:-( write failed: Input/output error
/dev/scd0: flushing cache
/dev/scd0: updating RMA
/dev/scd0: closing session

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/scd0=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:282889 -speed=16 -use-the-force-luke=bufsize:32m 

mkisofs
-----------------------
282889
I: -input-charset not specified, using utf-8 (detected in locale settings)
  0.18% done, estimate finish Sat Jun 14 14:08:07 2008
  0.36% done, estimate finish Sat Jun 14 14:08:07 2008
  0.53% done, estimate finish Sat Jun 14 14:08:07 2008
  0.71% done, estimate finish Sat Jun 14 14:08:07 2008
  0.89% done, estimate finish Sat Jun 14 14:08:07 2008
  1.06% done, estimate finish Sat Jun 14 14:08:07 2008
  1.24% done, estimate finish Sat Jun 14 14:08:07 2008
  1.41% done, estimate finish Sat Jun 14 14:08:07 2008
  1.59% done, estimate finish Sat Jun 14 14:08:07 2008
  1.77% done, estimate finish Sat Jun 14 14:09:03 2008
  1.95% done, estimate finish Sat Jun 14 14:08:58 2008
  2.12% done, estimate finish Sat Jun 14 14:08:54 2008
  2.30% done, estimate finish Sat Jun 14 14:08:50 2008
  2.47% done, estimate finish Sat Jun 14 14:08:47 2008
  2.66% done, estimate finish Sat Jun 14 14:08:44 2008
  2.83% done, estimate finish Sat Jun 14 14:08:42 2008
  3.01% done, estimate finish Sat Jun 14 14:08:40 2008
  3.18% done, estimate finish Sat Jun 14 14:08:38 2008
  3.36% done, estimate finish Sat Jun 14 14:08:36 2008
  3.54% done, estimate finish Sat Jun 14 14:08:35 2008
  3.71% done, estimate finish Sat Jun 14 14:08:33 2008
  3.89% done, estimate finish Sat Jun 14 14:08:32 2008
  4.07% done, estimate finish Sat Jun 14 14:08:31 2008
  4.25% done, estimate finish Sat Jun 14 14:08:30 2008
  4.42% done, estimate finish Sat Jun 14 14:08:29 2008
  4.60% done, estimate finish Sat Jun 14 14:08:28 2008
  4.78% done, estimate finish Sat Jun 14 14:08:27 2008
  4.95% done, estimate finish Sat Jun 14 14:08:27 2008
  5.13% done, estimate finish Sat Jun 14 14:08:26 2008
  5.30% done, estimate finish Sat Jun 14 14:08:25 2008
  5.48% done, estimate finish Sat Jun 14 14:08:25 2008
  5.66% done, estimate finish Sat Jun 14 14:08:24 2008
  5.83% done, estimate finish Sat Jun 14 14:17:49 2008
  6.01% done, estimate finish Sat Jun 14 14:18:06 2008
  6.19% done, estimate finish Sat Jun 14 14:17:48 2008
  6.37% done, estimate finish Sat Jun 14 14:17:32 2008
  6.54% done, estimate finish Sat Jun 14 14:17:17 2008
  6.72% done, estimate finish Sat Jun 14 14:17:02 2008
  6.90% done, estimate finish Sat Jun 14 14:17:46 2008
  7.07% done, estimate finish Sat Jun 14 14:17:32 2008
  7.25% done, estimate finish Sat Jun 14 14:17:46 2008
  7.43% done, estimate finish Sat Jun 14 14:17:32 2008
  7.60% done, estimate finish Sat Jun 14 14:17:32 2008
  7.78% done, estimate finish Sat Jun 14 14:17:19 2008
  7.95% done, estimate finish Sat Jun 14 14:17:07 2008
  8.13% done, estimate finish Sat Jun 14 14:17:32 2008

mkisofs calculate size command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -print-size -quiet -volid coches -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-josep/k3bdgVdFb.tmp -rational-rock -hide-list /tmp/kde-josep/k3bbaRm9a.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-josep/k3bVhQoJb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-josep/k3bt8ONYb.tmp 

mkisofs command:
-----------------------
/usr/bin/genisoimage -gui -graft-points -volid coches -volset  -appid K3B THE CD KREATOR (C) 1998-2006 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-josep/k3bGVZUvb.tmp -rational-rock -hide-list /tmp/kde-josep/k3bLVWFac.tmp -joliet -joliet-long -hide-joliet-list /tmp/kde-josep/k3b34FFYb.tmp -no-cache-inodes -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-josep/k3byai5Ga.tmp

---

### Post by prostata on 2008-06-14
Per cert, ara tampoc em deixa treballar amb CD's, diu que si que grava, però res de res i el pitjor es que em deixa els suports inservibles....:confused:

---

### Post by prostata on 2008-06-14
Més; he instalat Gnomebaker, en principi Ok però..per gravar un Cd de 700Mb ha trigat 25 minuts ¿és normal?, jo diria que no.. un DVD amb 1.5 Gb ha trigat la meitat de temps, ¿és normal?, jo diria que no...¿que pot estar passant a l'interior del meu Hardy???

gràcies

---

### Post by Pondus on 2008-10-23
A mi em passa exactament el mateix. Has aconseguit arreglar-ho?

---

### Post by quitus on 2008-10-23
Jo vaig tenir conflictes amb uns dvd i baixant la velocitat de l'escriptura s'hem va arreglar. En comptes d'automàtic proveu 4x  

salut

---

