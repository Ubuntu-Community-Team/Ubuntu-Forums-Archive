---
title: "k3b problem - fail to burn audio-cds"
date: 2005-02-25
forum: Desktop Environments
---

### Post by andbert on 2005-02-25
I recently installed k3b using synaptic.

I run it with the following command:
gksudo k3b

I have a usb LITE_ON LXR40243.
The program finds the cd writer, but spits out a debugging report immediately:

Devices
-----------------------
LITE-ON LXR-40243 US02 (/dev/scd0, ) at  [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
HL-DT-ST DVD-ROM GDR8162B 0017 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

System
-----------------------
K3b Version: 0.11.20
KDE Version: 3.3.2
QT Version:  3.3.3
Kernel:      2.6.10-3-686

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.10-3-686
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 0 = CD-DA
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
/usr/bin/cdrecord: No such file or directory. Cannot open '/dev/sg*'. Cannot open SCSI driver.
/usr/bin/cdrecord: For possible targets try 'cdrecord -scanbus'.
/usr/bin/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/cdrecord: 
/usr/bin/cdrecord: For more information, install the cdrtools-doc
/usr/bin/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=1,0,0 speed=40 -dao driveropts=burnfree -eject -useinfo -pad -shorttrack -audio /tmp/kde-root/k3b_audio_0_01.inf /tmp/kde-root/k3b_audio_0_02.inf /tmp/kde-root/k3b_audio_0_03.inf /tmp/kde-root/k3b_audio_0_04.inf /tmp/kde-root/k3b_audio_0_05.inf /tmp/kde-root/k3b_audio_0_06.inf /tmp/kde-root/k3b_audio_0_07.inf /tmp/kde-root/k3b_audio_0_08.inf /tmp/kde-root/k3b_audio_0_09.inf /tmp/kde-root/k3b_audio_0_10.inf /tmp/kde-root/k3b_audio_0_11.inf /tmp/kde-root/k3b_audio_0_12.inf /tmp/kde-root/k3b_audio_0_13.inf /tmp/kde-root/k3b_audio_0_14.inf /tmp/kde-root/k3b_audio_0_15.inf /tmp/kde-root/k3b_audio_0_16.inf /tmp/kde-root/k3b_audio_0_17.inf /tmp/kde-root/k3b_audio_0_18.inf 

Any input please how I can correct this problem?
Thanks!

---

### Post by andbert on 2005-03-01
*bump* 
anyone?
my LiteOn LXR appears when i insert a data cd, but it wont mount as a writer it seems like.

---

