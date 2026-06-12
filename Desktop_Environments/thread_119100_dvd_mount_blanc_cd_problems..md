---
title: "dvd mount blanc cd problems."
date: 2006-01-18
forum: Desktop Environments
---

### Post by syklitengutt on 2006-01-18
Hi... I use xfce and when i go into the xffstab manager and try to mount a 
empty dvd I get this error:
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

smesg | tails sais:
[4311472.270000] hdc: rw=0, want=68, limit=4
[4311472.270000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4311504.074000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311504.074000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311504.180000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311504.180000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311576.915000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4311576.915000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4311577.034000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4311577.034000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.


I can mount cds and dvds this way...

and when I try to install something troug cdrom0 I get this error:
chris@chris:/media/cdrom0$ ./linux-installer.sh
bash: ./linux-installer.sh: /bin/sh: bad interpreter: Permission denied
chris@chris:/media/cdrom0$

---

### Post by syklitengutt on 2006-01-18
fired up gnome and started k3b.
Tried to burn a dvd and got this error:
System
-----------------------
K3b Version: 0.12.7

KDE Version: 3.4.3
QT Version:  3.3.4
Kernel:      2.6.12-10-386
Devices
-----------------------
LITE-ON DVDRW SOHW-1693S KS04 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Sequential; DVD-R Dual Layer Sequential; DVD-RW Restricted Overwrite; DVD-RW Sequential; DVD+RW; DVD+R; DVD+R Double Layer; CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Restricted Overwrite]

K3b
-----------------------
Size of filesystem calculated: 0

Used versions
-----------------------
mkisofs: 2.1-unofficial-iconv

mkisofs
-----------------------
/usr/bin/X11/mkisofs: Warning: -follow-links does not always work correctly; be careful.
Warning: Disabling Joliet support for DVD-Video.
/usr/bin/X11/mkisofs: No such file or directory. Faild to open /tmp/kde-chris/k3bVideoDvd0//VIDEO_TS/VIDEO_TS.IFO
/usr/bin/X11/mkisofs: Can't open VMG info for '/tmp/kde-chris/k3bVideoDvd0/'.
/usr/bin/X11/mkisofs: Unable to parse DVD-Video structures.
/usr/bin/X11/mkisofs: Unable to make a DVD-Video image

---

### Post by syklitengutt on 2006-01-18
I can burn a movie but not a dvd... why?

---

### Post by syklitengutt on 2006-01-19
I can burn data dvds and data and music cds but not dvds.
I can also burn vcds...

any ideas on howto get burning dvd movues working?
i have k3b and the errors I get is posted above

---

