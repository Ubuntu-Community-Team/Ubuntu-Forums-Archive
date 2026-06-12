---
title: "cd writer doesn't work at all !"
date: 2005-11-03
forum: Desktop Environments
---

### Post by blabla123 on 2005-11-03
Hi,

I've got a problem;
i can't write cd's! Not with Nautilus, Gnomebaker or Graveman.

**this is my fstab**
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
#/dev/hda1       /media/windows     ntfs    nls=utf8,umask=0222 0       0
/dev/hda5       /media/win_linux    vfat    iocharset=utf8,umask=000   0       0
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0  udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


**this is what hdparm says:**
hdparm -i /dev/hdd

/dev/hdd:

 Model=AOPEN CD-RW CRW4852 1.02 20031030, FwRev=1.02, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:

 * signifies the current active mode
[B]
This is what cdrecord says:[/B]
cdrecord dev=/dev/hdd -scanbus
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-9-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus1:
        1,0,0   100) *
        1,1,0   101) 'AOPEN   ' 'CD-RW CRW4852   ' '1.02' Removable CD-ROM
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *

I get no error when trying to burn with the gui burn progs, the drive does nothing, the prog hangs. I didn't try commandline burning (too complicated for an ex-windows user ;)  ).

Anyone got an idea???

gr

---

### Post by Ampersand on 2005-11-03
Looks like you need to be root to burn cds. Try running
```
sudo gnomebaker
```
from a terminal (or sudo followed by any other cd burning application).

---

### Post by blabla123 on 2005-11-03
Ampersand,

thanks for your reply, but..............

it didn't work. I did 

sudo gnomebaker, tried to make a data cd, the console gave me this message:

Xlib: unexpected async reply (sequence 0x28a74)!

then gnomebaker hang, had to kill it.

:( 

gr

---

### Post by rjwood on 2005-11-03
I'm having the same problem

---

### Post by phogen on 2005-11-06
I'm  having the same problem as well.  Can anyone help us?

---

### Post by thnogueira on 2005-11-08
Hey guys, 

same here.

Another breezy stuff...

Probably the solution is
 Downloadable Serial Number:  19.99 USD  (NeroLinux)

and get even more close to windows.

I'm really concerned about Linux future. 12 year ago it was very difficult to have all the system working but once you got it, it used to last almost forever. Nowadays we expend 3 months making it work until the next "stable" version is released. It's not Ubuntu. It's general.

Sorry. No help.:-#


EDIT: Well I don't beleive in god, but it seems he read this words. I don't exactly know how but I got it working. Let me tell what I did:
After writing this post I installed NeroLinux and when ran it I got a message I haven't DMA enabled on CD-ROM Device.
I checked the file /etc/hdparm.conf and yes I already had the below lines at the end of file (from ubuntuguide.org)

```

/dev/cdrom {
       dma = on
}

```

I decided to run the command again (again from ubuntuguide): 

```

sudo hdparm -d1 /dev/cdrom

```

and well, it's working. I rebooted the system and it was still working without the hdparm command.After that, I completely removed nerolinux and... Well I'm wating... Yes!!!
Success.

 My guess is that you don't need to install nerolinux, but make shure DMA is enabled on CD-ROM device.
I hope it work for you, guys.

---

### Post by rjwood on 2005-11-08
[quote=thnogueira]Hey guys, 

same here.

Another breezy stuff...

Probably the solution is
 Downloadable Serial Number:  19.99 USD  (NeroLinux)

and get even more close to windows.

I'm really concerned about Linux future. 12 year ago it was very difficult to have all the system working but once you got it, it used to last almost forever. Nowadays we expend 3 months making it work until the next "stable" version is released. It's not Ubuntu. It's general.

Sorry. No help.:-#


EDIT: Well I don't beleive in god, but it seems he read this words. I don't exactly know how but I got it working. Let me tell what I did:
After writing this post I installed NeroLinux and when ran it I got a message I haven't DMA enabled on CD-ROM Device.
>  I checked the file /etc/hdparm.conf and yes I already had the below lines at the end of file (from ubuntuguide.org)

```

/dev/cdrom {
       dma = on
}

``` 
I decided to run the command again (again from ubuntuguide): 

```

sudo hdparm -d1 /dev/cdrom

``` 
and well, it's working. I rebooted the system and it was still working without the hdparm command.After that, I completely removed nerolinux and... Well I'm wating... Yes!!!
Success.

 My guess is that you don't need to install nerolinux, but make shure DMA is enabled on CD-ROM device.
I hope it work for you, guys.[/quote]
would you mind posting your /etc/hdparm.conf file so I can see it. I don't quite understand how you fixed it.

---

### Post by thnogueira on 2005-11-09
My hdparm.conf:

```

## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

#/dev/cdroms/cdrom0 {
#	dma = on		   
#	interrupt_unmask = on
#	io32_support = 0
#}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}
/dev/cdrom {
       dma = on
	interrupt_unmask = on
	io32_support = 0
}


```

I couldn't realize how it's working too. That why I explained everithing I've made between last unsuccessful try and the first one it went right. I hope anybody else can reproduct this behavior. If you want any other information, please let me know.

BTW - Am I running hdparm on my hds hda and hdb? Taking a look at the above file it seems I'm not...

---

### Post by GrayMagiker on 2005-11-12
Awesome, this is just what my computer needed apparently.  Thanks so much for helping out and finding a simple solution to the problem.

---

### Post by blabla123 on 2005-11-25
still doesn't work for me :( 

this is what my hdparm looks like (first it said /dev/cdrom and /dev/cdrom1, but that didn't work so i changed iet to /dev/hdc and /dev/hdd. But that didn't work either):
> ## This is the default configuration for hdparm for Debian.  It is a 
## rather simple script, so please follow the following guidelines :)
## Any line that begins with a comment is ignored - add as many as you 
## like.  Note that an in-line comment is not supported.  If a line 
## consists of whitespace only (tabs, spaces, carriage return), it will be
## ignored, so you can space control fields as you like.  ANYTHING ELSE
## IS PARSED!!  This means that lines with stray characters or lines that 
## use non # comment characters will be interpreted by the initscript.  
## This has probably minor, but potentially serious, side effects for your 
## hard drives, so please follow the guidelines.  Patches to improve 
## flexibilty welcome.  Please read /usr/share/doc/hdparm/README.Debian for 
## notes about known issues, especially if you have an MD array.
##
## Note that if the init script causes boot problems, you can pass 'nohdparm' 
## on the kernel command line, and the script will not be run.
##
## Uncommenting the options below will cause them to be added to the DEFAULT
## string which is prepended to options listed in the blocks below.
##
## If an option is listed twice, the second instance replaces the first.
##
## /sbin/hdparm is not run unless a block of the form:
##      DEV {
##         option
##         option
##         ...
##      }
## exists.  This blocks will cause /sbin/hdparm OPTIONS DEV to be run.
## Where OPTIONS is the concatenation of all options previously defined
## outside of a block and all options defined with in the block.

# -q be quiet
quiet 
# -a sector count for filesystem read-ahead
#read_ahead_sect = 12
# -A disable/enable the IDE drive's read-lookahead feature
#lookahead = on
# -b bus state
#bus = on
# -B apm setting
#apm = 255
# -c enable (E)IDE 32-bit I/O support - can be any of 0,1,3
#io32_support = 1
# -d disable/enable the "using_dma" flag for this drive
#dma = off
# -D enable/disable the on-drive defect management
#defect_mana = off
# -E cdrom speed
#cd_speed = 16
# -k disable/enable the "keep_settings_over_reset" flag for this drive
#keep_settings_over_reset = off
# -K disable/enable the drive's "keep_features_over_reset" flag
#keep_features_over_reset = on
# -m sector count for multiple sector I/O
#mult_sect_io = 32
# -P maximum sector count for the drive's internal prefetch mechanism
#prefetch_sect = 12
# -r read-only flag for device
#read_only = off
# -S standby (spindown) timeout for the drive
#spindown_time = 24
# -u interrupt-unmask flag for the drive
#interrupt_unmask = on
# -W Disable/enable the IDE drive's write-caching feature
#write_cache = off
# -X IDE transfer mode for newer (E)IDE/ATA2 drives
#transfer_mode = 34
# -y force to immediately enter the standby mode
#standby
# -Y force to immediately enter the sleep mode
#sleep
# -Z Disable the power-saving function of certain Seagate drives
#disable_seagate
# -M Set the acoustic management properties of a drive
#acoustic_management
# -p Set the chipset PIO mode
# chipset_pio_mode

# Root file systems.  Please see README.Debian for details
# ROOTFS = /dev/hda

## New note - you can use straight hdparm commands in this config file 
## as well - the set up is ugly, but it keeps backwards compatibility
## Additionally, it should be noted that any blocks that begin with 
## the keyword 'command_line' are not run until after the root filesystem
## is mounted.  This is done to avoid running blocks twice.  If you need 
## to run hdparm to set parameters for your root disk, please use the 
## standard format.

#Samples follow:
#First three are good for devfs systems, fourth one for systems that do 
#not use devfs.  The fifth example uses straight hdparm command line
#syntax.  Any of the blocks that use command line syntax must begin with
#the keyword 'command_line', and no attempt is made to validate syntax.  
#It is provided for those more comfortable with hdparm syntax. 

#/dev/discs/disc0/disc {
#	mult_sect_io = 16
#	write_cache = off
#	spindown_time = 240
#}

#/dev/discs/disc1/disc {
#	mult_sect_io = 32
#	spindown_time = 36
#	write_cache = off
#}

/dev/hdc {
	dma = on		   
	interrupt_unmask = on
	io32_support = 0
}

/dev/hdd {
	dma = on		   
	interrupt_unmask = on
	io32_support = 0
}

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

#command_line {
#       hdparm -q -m16 -q -W0 -q -d1 /dev/hda
#}


and this is what hdparm -i /dev/hdd says:
> /dev/hdd:

 Model=AOPEN CD-RW CRW4852 1.02 20031030, FwRev=1.02, SerialNo=
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 *udma2
 AdvancedPM=no
 Drive conforms to: ATA/ATAPI-5 T13 1321D revision 3:

 * signifies the current active mode


Anyone got any other suggestions??? 

gr

---

### Post by az on 2005-11-25
"Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted"

That is a common error from cdrecord.  Cdrecord is a mess.  A few years back, Joerg Schilling even put a comment in the middle of the code saying that no one was allowed to change certain things because he was sick of getting emails about the problems that it caused.

That caused cdrecord to become non-free and it stirred up a big fuss.  He changed it in later version to make it continue to be GPL licenced, but the point is that there are a few lasting structural issues with cdrecord that have to get worked around by the distro.   That is the reason for those two error messages (pretty much) and that is *not* the reason you cannot burn.

I think there was plans to make a burning infrastructure in HAL that did not rely on cdrecord but I do not know what happend to that.

What is relevant in the error log is the last few lines before it quits on you.  Can you post the whole message?

Do you have burnfree on?

---

### Post by blabla123 on 2005-11-25
Hi,

i managed to burn an audio cd with cdrecord, but.........
-cdrecord gave me several errors
-one song has been burned twice (12 songs on the cd)
-finalizing the process took a long time

see next output:
>  cdrecord dev=/dev/hdd -eject speed=20 -pad -audio *.wav 
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent default s.
cdrecord: Continuing in 5 seconds...
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c1 .91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'AOPEN   '
Identifikation : 'CD-RW CRW4852   '
Revision       : '1.02'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R96R
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Error: Cannot gain SYS_RAWIO capability.Is cdrecord installed SUID root?
: Operation not permitted
Starting to write CD/DVD at speed 48 in real TAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Turning BURN-Free off
Track 01: Total bytes read/written: 48437088/48437088 (20594 sectors).
Track 02: Total bytes read/written: 52426080/52426080 (22290 sectors).
Track 03: Total bytes read/written: 41959680/41959680 (17840 sectors).
Track 04: Total bytes read/written: 41439888/41439888 (17619 sectors).
Track 05: Total bytes read/written: 41439888/41439888 (17619 sectors).
Track 06: Total bytes read/written: 55269648/55269648 (23499 sectors).
Track 07: Total bytes read/written: 37723728/37723728 (16039 sectors).
Track 08: Total bytes read/written: 64727040/64727040 (27520 sectors).
Track 09: Total bytes read/written: 52959984/52959984 (22517 sectors).
Track 10: Total bytes read/written: 33906432/33906432 (14416 sectors).
Track 11: Total bytes read/written: 50629152/50629152 (21526 sectors).
cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 03 6A 37 00 00 1B 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 04 00 03 67 19 0C 00 00 00 00 09 02 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x02 (focus servo failure) Fru 0x0
Sense flags: Blk 223001 (valid)
resid: 63504
cmd finished after 11.286s timeout 40s
write track data: error after 1524096 bytes
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.
cdrecord: Success. flush cache: scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: F0 00 04 00 03 67 19 0C 00 00 00 00 09 02 00 00
Sense Key: 0x4 Hardware Error, Segment 0
Sense Code: 0x09 Qual 0x02 (focus servo failure) Fru 0x0
Sense flags: Blk 223001 (valid)
cmd finished after 45.929s timeout 120s
Trouble flushing the cache


so it works, but not as it should.........

gr

---

### Post by blabla123 on 2005-11-25
Hey, that's strange.................
Gnomebaker still doesn't work, but Graveman does!!!!!!!!!!!!!

Am i the only one that doesn't understand it?

btw These things make former windows users (including me) go back to windows  very fast! It took me several hours before i was able to burn a (audio-) cd. And if you compare that with windows.......... 
I used to have Archlinux on my pc, if you install that you know you have to configure everything by hand. But Ubuntu claims to be a userfriendly Linux distro. I think this should work out of the box (and it always has with most major distro's (including Ubuntu), so what's going on?). 
btw2  the cdburner was the only problem i have/had with Ubuntu, so i still think it's a superb distro!!!!!!!

gr

---

