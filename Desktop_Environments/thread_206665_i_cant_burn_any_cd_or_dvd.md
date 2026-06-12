---
title: "i cant burn any cd or dvd"
date: 2006-06-30
forum: Desktop Environments
---

### Post by greenfrognet on 2006-06-30
[B]Hi friends, i have a problem what a cant find in internet
I have Ubuntu 6.06 but I can&#8217;t burn any cd or dvd, I try with bonfire, gnomebacker, k3b, without results. But I tests my drives and working fine in windows whit the same disc, whit NeroLinux I burn fine but I prefers open source software [/B]

**This is my fstab**

 # /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc               /proc           proc    defaults        0       0
 /dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
 /dev/hda1       /boot           ext3    defaults        0       2
 /dev/hda3       /home           ext3    defaults        0       2
  /dev/sda1       /media/sda1     ntfs
 defaults,nls=utf8,umask=007,gid=46 0       1
 /dev/hda4       none            swap    sw              0       0
 /dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
 /dev/hdd        /media/dvdrecorder   udf,iso9660 user,noauto     0       0

**this is my /media/**

 lrwxrwxrwx 1 root root       6 2006-06-27 21:58 cdrom -> cdrom0
 drwxr-xr-x 2 root root    4096 2006-06-27 21:58 cdrom0
 drwxr-xr-x 2 root root     136 2006-06-26 10:55 dvdrecorder
 dr-xr-x--- 1 root plugdev 8192 2006-06-27 00:34 sda1

**This is my /var/log/messages,**

hdc: HL-DT-ST GCE-8527B, ATAPI CD/DVD-ROM drive (LG CD/RW)
hdd: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive (DVDRW)

**this is de message log of  Bonfire**

Jun 29 09:31:30 skynet kernel: [17184672.076000] cdrom: This disc doesn't have any tracks I recognize!
Jun 29 09:31:32 skynet kernel: [17184674.108000] cdrom: This disc doesn't have any tracks I recognize! 
Jun 29 09:31:41 skynet gconfd (root-8248): comenzando (versión  2.14.0), pid 8248 usuario «root»
Jun 29 09:31:41 skynet gconfd (root-8248): Se resolvió la dirección «xml:readonly:/etc/gconf/gconf.xml.mandatory» a una fuente de configuración de sólo lectura en la posición 0 
Jun 29 09:31:41 skynet gconfd (root-8248): Se resolvió la dirección «xml:readwrite:/root/.gconf» a una fuente de configuración escribible en la posición 1
Jun 29 09:31:41 skynet gconfd (root-8248): Se resolvió la dirección «xml:readonly:/etc/gconf/gconf.xml.defaults» a una fuente de configuración de sólo lectura en la posición 2 
Jun 29 09:31:41 skynet gconfd (root-8248): Se resolvió la dirección «xml:readonly:/var/lib/gconf/debian.defaults» a una fuente de configuración de sólo lectura en la posición 3
Jun 29 09:31:41 skynet gconfd (root-8248): Se resolvió la dirección «xml:readonly:/var/lib/gconf/defaults» a una fuente de configuración de sólo lectura en la posición 4 
Jun 30 09:32:18 skynet gconfd (root-8248): El servidor GConf no está en uso, cerrándolo.
Jun 30 09:32:18 skynet gconfd (root-8248): Finalizando
Jun 30 09:33:14 skynet kernel: [17184778.852000] hdd: DMA timeout retry 
Jun 30 09:33:19 skynet kernel: [17184784.056000] hdd: status timeout: status=0xd0 { Busy }
Jun 30 09:33:19 skynet kernel: [17184784.056000] ide: failed opcode was: unknown
Jun 30 09:33:19 skynet kernel: [17184784.104000 ] hdd: ATAPI reset complete

**this is de message log of  de K3B**
HL-DT-ST CD-RW GCE-8527B 1.02 (/dev/hdc, ) at /media/cdrom0 [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; En bruto; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R] 
LITE-ON DVDRW SOHW-1693S KS0A (/dev/hdd, ) at [CD-R; CD-RW; CD-ROM; DVD-ROM; DVD-R; DVD-RW; DVD-R DL; DVD+R; DVD+RW; DVD+R DL] [DVD-ROM; DVD-R Secuencial; DVD-R Doble capa secuencial; DVD-R doble capa salteado; DVD-RW sobreescritura restringida; DVD-RW Secuencial; DVD+RW; DVD+R; DVD+R doble capa; CD-ROM; CD-R; CD-RW] [SAO; TAO; En bruto; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96P; RAW/R96R; Sobreescritura restringida; Salto de capa]
K3b
-----------------------
Size of filesystem calculated: 2156390
Used versions
-----------------------
growisofs: 5.21
growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/hdd obs=32k seek=0'
/dev/hdd: "Current Write Speed" is 8.2x1385KBps.
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
0/4416286720 ( 0.0%) @0x, remaining ????
 [B]unable to WRITE@LBA=0h: Input/output error
 write failed: Input/output error[/B]
growisofs command:
-----------------------
/usr/bin/X11/growisofs -Z /dev/hdd=/dev/fd/0 -use-the-force-luke=notray -use-the-force-luke=tty -use-the-force-luke=tracksize:2156390 -dvd-compat -speed=8 
mkisofs
-----------------------
/usr/bin/X11/mkisofs: Warning: -follow-links does not always work correctly; be careful.
Warning: Disabling Joliet support for DVD-Video.
/usr/bin/X11/mkisofs: Warning: -follow-links does not always work correctly; be careful.
Warning: Disabling Joliet support for DVD-Video.
2156390
/usr/bin/X11/mkisofs: Warning: -follow-links does not always work correctly; be careful.
Warning: Disabling Joliet support for DVD-Video.
INFO: UTF-8 character encoding detected by locale settings.
Assuming UTF-8 encoded filenames on source filesystem,
use -input-charset to override.
0.02% done, estimate finish Sat Jun 24 22:50:10 2006
0.05% done, estimate finish Sat Jun 24 23:25:34 2006
0.07% done, estimate finish Sat Jun 24 23:13:57 2006
0.09% done, estimate finish Sat Jun 24 23:08:07 2006
mkisofs command:
-----------------------
/usr/bin/X11/mkisofs -gui -graft-points -volid K3b data project -volset -appid K3B THE CD KREATOR (C) 1998-2005 SEBASTIAN TRUEG AND THE K3B TEAM -publisher -preparer -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-dino/k3bLRbS3b.tmp -rational-rock -hide-list /tmp/kde-dino/k3bdqvXla.tmp -joliet -hide-joliet-list /tmp/kde-dino/k3bOKisbc.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-dino/k3bC24Eec.tmp -dvd-video -f /tmp/kde-dino/k3bVideoDvd0 
this is de message log of  GnomeBaker
Jun 30 09:39:44 skynet kernel: [17185168.980000] hdd: DMA timeout retry
Jun 30 09:39:50 skynet kernel: [17185174.184000] hdd: status timeout: status=0xd0 { Busy } 
Jun 30 09:39:50 skynet kernel: [17185174.184000] ide: failed opcode was: unknown
Jun 30 09:39:50 skynet kernel: [17185174.232000] hdd: ATAPI reset complete

[COLOR="DarkRed"]HEEEEEELLLLLLPPPPPPPP.
Thanks and sorry for the long message and my awful English[/COLOR]

---

