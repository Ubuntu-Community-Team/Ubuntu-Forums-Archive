---
title: "cdrecord -scanbus does not work with dapper's kernel Linux-2.6.15-26-386"
date: 2006-07-22
forum: Desktop Environments
---

### Post by beforewisdom on 2006-07-22
Hi All;

The other day the dapper update manager told me to install the latest kernel.  No problems until I tried to use cdrecord -scanbus.   Will not work with the current kernel.

Is there a substitute for cdrecord -scanbus?  I'm trying to copy an existing VCD and I seem to need this step to find out what codes my devices are list under.  Is there another way to accomplish this goal?

Below is the error message I received:

=================================================
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
steve@00400582fa8a:~$

==================================================

---

### Post by moma on 2006-07-22
Try this:

$ cdrecord  dev=ATAPI  --scanbus

Example usage:
$ cdrecord -v -eject dev=ATAPI:0,0,0 filename.iso

---

### Post by beforewisdom on 2006-07-22
I got the same exact error message.

Thanks anyway.

---

### Post by Dominus Suus on 2006-07-23
Ditto, I have the same problem (but I can't remember the last time I burned a CD before the upgrade)

I've been reading up on the problem and some places suggest that I dive into /etc/modprobe.d and start writing aliases for the ide-scsi module - but that was back in the Warty days.  I don't know exactly what I'm doing when it comes to /etc so I'd rather someone a little more knowledgeable attempt first.  Furthermore, since Ubuntu is supposed to 'work out of the box' (I'll hold my tongue on that one), I'm wondering whether the solution lies in something simpler than running around config files.

---

### Post by sutterp on 2006-07-30
I don't know if it is polite or custom in this forum to revive an old thread, if not, my apologies.

I had the same problems, I fixed them the following way:

Step 1:

Add hdx=ide-scsi to the kernel line in /boot/grub/menu.lst, where hdx is the drive of yoyr cd/dvd reader/writer

> kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 hdc=ide-scsi ro quiet splash

Step 2:

Edit /etc/modules and add all lines that begin with ide-

> ide-cd
ide-disk
ide-generic
ide-core
ide-scsi
lp
mousedev
psmouse


Step 3:

Re-boot your system

This should give you ide-scsi support for your cd-rom reader/writer, and cdrecord should now know about sg/scd devices, cdrecord -scanbus reports the correct devices.

You need to change the device (most likely hdx) to whatever cdrecord -scanbus reports as your drive in /etc/fstab.

Most cdrecord commands work now, except the actual burning. Here are the messages I get

> root@james:~# cdrecord -dev=0,0,0 -speed=24 -data -dao -v /bca/backup/Backup-to-cd-2006-07-30.iso
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c      1.91 04/06/ 17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 2
Response Format: 2
Capabilities   :
Vendor_info    : 'HL-DT-ST'
Identifikation : 'CD-RW GCE-8526B '
Revision       : '1.03'
Device seems to be: Generic mmc CD-RW.
Current: 0x000A
Profile: 0x000A (current)
Profile: 0x0009
Profile: 0x0008
Profile: 0x0002 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1951488 = 1905 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data    73 MB
Total size:       84 MB (08:21.65) = 37624 sectors
Lout start:       84 MB (08:23/49) = 37624 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 6
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11078 (97:34/22)
  ATIP start of lead out: 336075 (74:43/00)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  2T speed low:  0 (reserved val  5) 2T speed high:  0 (reserved val 12)
  power mult factor: 3 5
  recommended erase/write power: 3
  A1 values: 02 3A B0
  A2 values: 5C C6 26
Disk type:    Phase change
Manuf. index: 11
Manufacturer: Mitsubishi Chemical Corporation
Trying to clear drive status.
cdrecord: Drive needs to reload the media to return to proper status.
cdrecord: Cannot get next writable address for 'invisible' track.
cdrecord: This means that we are checking recorded media.
cdrecord: This media cannot be written in streaming mode anymore.
cdrecord: If you like to write to 'preformatted' RW media, try to blank the media first.
Starting to write CD/DVD at speed 4 in real SAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Performing OPC...
Sending CUE sheet...
cdrecord: CUE sheet not accepted. Retrying with minimum pregapsize = 1.
cdrecord: Input/output error. send_cue_sheet: scsi sendcmd: no error
CDB:  5D 00 00 00 00 00 00 00 20 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 06 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x30 Qual 0x06 (cannot format medium - incompatible medium) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.000s timeout 200s
cdrecord: CUE sheet still not accepted. Please try to write in RAW (-raw96r) mode.
cdrecord: Cannot send CUE sheet.
cdrecord: Could not write Lead-in.
Writing  time:    9.170s
cdrecord: fifo had 64 puts and 0 gets.
cdrecord: fifo was 0 times empty and 0 times full, min fill was 100%.


and in /var/log/messages I get 
> Jul 30 20:41:22 localhost kernel: [17180170.580000] end_request: I/O error, dev sr0, sector 0
Jul 30 20:42:31 localhost kernel: [17180236.628000] hdd: irq timeout: status=0xd0 { Busy }
Jul 30 20:42:31 localhost kernel: [17180236.628000] ide: failed opcode was: unknown
Jul 30 20:44:00 localhost kernel: [17180328.596000] hda: dma_timer_expiry: dma status == 0x21
Jul 30 20:44:41 localhost kernel: [17180338.596000] hda: DMA timeout error
Jul 30 20:44:41 localhost kernel: [17180338.596000] hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }


Anybody out there who knows how to fix this?

Is it a dma problem, should dma be turned off? I'm not sure the drive supportd dma.

Peter

---

### Post by Dubbayoo on 2006-07-30
seems to be okay here

> steve@ubu:~$ **uname -r**
2.6.15-26-686
steve@ubu:~$ **sudo cdrecord -scanbus**
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-26-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
Linux sg driver version: 3.5.33
Using libscg version 'debian-0.8debian2'.
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
scsibus0:
        0,0,0     0) 'FUJITSU ' 'MAN3367MP       ' '0108' Disk
        0,1,0     1) *
        0,2,0     2) *
        0,3,0     3) *
        0,4,0     4) *
        0,5,0     5) 'PIONEER ' 'DVD-ROM DVD-305 ' '1.03' Removable CD-ROM
        0,6,0     6) *
        0,7,0     7) *
scsibus1:
        1,0,0   100) 'Apple   ' 'iPod            ' '1.62' Removable Disk
        1,1,0   101) *
        1,2,0   102) *
        1,3,0   103) *
        1,4,0   104) *
        1,5,0   105) *
        1,6,0   106) *
        1,7,0   107) *


---

### Post by drpaul on 2006-07-30
Is the difference that you have a scsi cdrom drive?

I'm running the standard 386 kernel and get the errors.

Paul

---

### Post by NicePics13 on 2006-07-30
You don't need scanbus or scsi emulation.
With the 2.6 kernel you type:

**cdrecord dev=/dev/hdc**

That's it. ;)

---

### Post by sutterp on 2006-07-30
No, that does not work, that's why I added scsi emulation. With it, cdrecord -scanbus reports correctly.

But either way I can't write, details as per my earlier post. Btw, I installed k3b and k3b does not work either.

It can't be the hardware, as this is a dual boot system on which I also run SuSE Linux, and both cdrecord and k3b run smoothly under SuSE. However, on SuSE I have DMA turned off for the cdrom, but I could not yet figure out how to do this in ubuntu.

---

### Post by NicePics13 on 2006-07-31
Edit */etc/hdparm.conf* to turn on/off DMA for your disks.

---

### Post by drpaul on 2006-07-31
Specifying dev=... on the command line generates more messages, but also allows -scanbus operation to report back. Wasn't necessary to turn off dma.

Paul

---

### Post by Dubbayoo on 2006-07-31
> **Dubbayoo said:**
> seems to be okay here


just noticed my burner is actually IDE and not shown there

> steve@ubu:~$ dmesg | grep hdc
[17179584.208000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:pio
[17179585.940000] hdc: PLEXTOR DVDR PX-712A, ATAPI CD/DVD-ROM drive
[17179586.304000] hdc: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 8192kB Cache, UDMA(33)


I have noticed that I can't burn audio cd's now. DVD iso's work fine; haven't tried other formats. Maybe I will try turning an audio cd into an iso first then burning that.

---

### Post by sutterp on 2006-07-31
Thank you,

I tried this, unfortunately I still get the same results.

Peter

---

### Post by kenquad on 2006-12-12
Hey, this thread was already resuscitated once, so why not again?:KS 

cdrecord newbie here, I'm trying to get my drive recognized so I can burn weekly incremental backups.  Here's the output of sudo cdrecord -scanbus:

```

cdrecord: Warning: Running on Linux-2.6.15-23-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

```

Here's the output of sudo cdrecord dev=/dev/hdc -checkdrive:

```

cdrecord: Warning: Running on Linux-2.6.15-23-server
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using inofficial version of libscg (debian-0.8debian2 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

Using libscg version 'debian-0.8debian2'.
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'SONY    '
Identifikation : 'CD-RW  CRX140E  '
Revision       : '1.0n'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R

```

As you can see, this drive is a few years old.  If anyone could point me in the right direction I would sure appreciate it!

Merry Christmas!

Kenquad

---

