---
title: "Impossible to burn dvd"
date: 2006-08-21
forum: Desktop Environments
---

### Post by marcostt on 2006-08-21
I use k3b (Kubuntu dapper). I can brun cd perfectly, but not dvd, no data, no video.

The error message trying to burn data dvd is:

```
System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-26-386
Devices
-----------------------
SONY DVD RW DW-Q30A YYS2 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Secuencial; DVD-R Doble capa secuencial; DVD-R doble capa salteado; DVD-RW sobreescritura restringida; DVD-RW Secuencial; DVD+RW; DVD+R; DVD+R doble capa; CD-ROM; CD-R; CD-RW] [SAO; TAO; En bruto; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Sobreescritura restringida; Salto de capa]

E-IDE CD-ROM 52X/AKH A64 (/dev/hdd, ) at  [CD-ROM] [Error] [Ninguno]
Used versions
-----------------------
growisofs: 5.21
mkisofs: 2.1-unofficial-iconv

growisofs
-----------------------
INFO: UTF-8 character encoding detected by locale settings.
 Assuming UTF-8 encoded filenames on source filesystem,
 use -input-charset to override.
/dev/hdc: "Current Write Speed" is 2.0x1385KBps.
:-[ WRITE@LBA=0h failed with SK=5h/ASC=64h/ACQ=00h]: Input/output error
:-( attempt to re-run with -dvd-compat -dvd-compat to engage DAO or apply full blanking procedure
:-( write failed: Input/output error

growisofs command:
-----------------------
/usr/bin/growisofs -Z /dev/hdc -use-the-force-luke=notray -use-the-force-luke=tty -overburn -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer  -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-marcos/k3b5Nqrhb.tmp -rational-rock -hide-list /tmp/kde-marcos/k3b1Frapa.tmp -joliet -hide-joliet-list /tmp/kde-marcos/k3blEZhkc.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-marcos/k3baemwxb.tmp 

```

Thanks in advance

---

### Post by metalsam on 2006-08-21
it says error next to the CD drive, are you trying to write to the CD drive ?

---

### Post by marcostt on 2006-08-21
Sorry, I dont understand what you mean...

---

