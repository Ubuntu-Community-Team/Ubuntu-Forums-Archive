---
title: "Sporadic CD mount problem in Dapper"
date: 2006-06-16
forum: Desktop Environments
---

### Post by Patb on 2006-06-16
Hi. A problem I had with Breezy ([http://ubuntuforums.org/showthread.php?t=104858](http://ubuntuforums.org/showthread.php?t=104858)) has only got worse with Dapper.  About once in every 5-6 boots, the indicator light on the CD-RW drive keeps blinking during boot (normally it is blinks a few times during the BIOS stage then goes off).  Dapper then locks up at the "mounting root file system" step.  The only solution is to reboot.  

Relevant line from my /etc/fstab reads:
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
Relevant lines from dmesg on a successful boot with no CD in the drive are:
```
[4294675.845000] hdc: HL-DT-ST GCE-8525B, ATAPI CD/DVD-ROM drive
[4294676.544000] hdc: ATAPI 52X CD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[4294676.544000] Uniform CD-ROM driver Revision: 3.20
[4294692.060000] cdrom: open failed.
```
Comments or suggestions would be welcome.  

Cheers, Pat.

---

