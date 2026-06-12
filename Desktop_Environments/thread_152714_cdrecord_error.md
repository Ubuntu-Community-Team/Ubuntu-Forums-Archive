---
title: "cdrecord error"
date: 2006-03-30
forum: Desktop Environments
---

### Post by dammit_jim on 2006-03-30
I am unable to burn CDs with K3B and I think I have traced the problem back to cdrecord. When I run cdrecord using the same arguments as K3B lists in its debug log I see the same error:

```
sudo /usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=16 -dao driveropts=burnfree -eject -data /tmp/kde-root/k3b_image.img
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

/usr/bin/cdrecord: Warning: Running on Linux-2.6.12-10-686
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
TOC Type: 1 = CD-ROM
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
/usr/bin/cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c     1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Driveropts: 'burnfree'
SCSI buffer size: 64512
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'OPTORITE'
Identifikation : 'CD-RW CW5207    '
Revision       : '150E'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A
Profile: 0x0009 (current)
Profile: 0x0008
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P RAW/R16 RAW/R96R
Drive buf size : 1575840 = 1538 KB
FIFO size      : 4194304 = 4096 KB
Track 01: data   644 MB
Total size:      739 MB (73:18.50) = 329888 sectors
Lout start:      740 MB (73:20/38) = 329888 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 4
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, low Beta category (A-) (2)
  ATIP start of lead in:  -12444 (97:16/06)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Manufacturer is unknown because of the orange forum embargo.
As the orange forum likes to get money for recent information,
it may be that this media does not use illegal manufacturer coding.
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 29961
Starting to write CD/DVD at speed 16 in real SAO mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Performing OPC...
Sending CUE sheet...
Writing pregap for track 1 at 329888
/usr/bin/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 05 08 BF 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 2C 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x2C Qual 0x00 (command sequence error) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 0.012s timeout 200s
write track pad data: error after 63488 bytes
BFree: 1538 K BSize: 1538 K
Starting new track at sector: 330038
Track 01:    0 of  644 MB written./usr/bin/cdrecord: faio_wait_on_buffer for writer timed out.
/usr/bin/cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 05 09 36 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
resid: 63488
cmd finished after 6.137s timeout 200s

write track data: error after 0 bytes
/usr/bin/cdrecord: A write error occured.
/usr/bin/cdrecord: Please properly read the error message above.
/usr/bin/cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.001s timeout 200s
Writing  time:  273.178s
Average write speed  16.3x.
Fixating...
/usr/bin/cdrecord: Success. flush cache: scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.001s timeout 200s
Trouble flushing the cache
/usr/bin/cdrecord: Success. test unit ready: scsi sendcmd: no error
CDB:  00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 3A 00 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x3A Qual 0x00 (medium not present) Fru 0x0
Sense flags: Blk 0 (not valid)
cmd finished after 0.001s timeout 200s
Fixating time:   26.041s
```

I think the issue may be the error ```
/usr/bin/cdrecord: faio_wait_on_buffer for writer timed out.
```

I'm using a fairly generic optorite cd-rewriter but K3B was working until recently (I think an upgrade may have bork'd it).

I'm using cdrecord 2.1.1a01 and K3b 0.12.7 on breezy.

Has anyone else encountered this problem? I've checked these forums (sorting out an earlier permissions issue) and read the cdrecord support but that mostly recommends installing Sun OS 10... Any help which doesn't involve switching away from Linux would be much appreciated.

---

### Post by rattking on 2006-03-30
Hi
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
makes it look like cdrecord or your burner dont know how to write to that type of disk..  do you have any other brands to try writing to? see if any media writes ok

---

