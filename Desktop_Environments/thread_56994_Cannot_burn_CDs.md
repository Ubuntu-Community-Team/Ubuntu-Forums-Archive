---
title: "Cannot burn CDs"
date: 2005-08-14
forum: Desktop Environments
---

### Post by Pig Monkey on 2005-08-14
I just attempted to burn the latest Knoppix iso with Graveman, but after it got to about 16%, I get an error that simply states "Operation failed". Any idea why?

I have [enabled dma](http://ubuntuguide.org/#speedupcddvdrom).

In the past (on Ubuntu, not any other distros) I've also had problem burning audio CDs. It always gets to about 30%, stops with an error, and spits the cd out. The resulting cd plays fine in any cd player, except that there's only about 30% of the audio there.

By the way, this is on a Dell 8600 laptop. The burner is a NEC CD/DVD+-RW ND-6500A

---

### Post by huh? on 2005-08-14
don't know anything about graveman....can you try and use k3b ?  it works for me

---

### Post by tuxfan99 on 2005-08-15
GnomeBaker says it's a buffer underrun:
```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 3 = CD-ROM XA mode 2
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : '_NEC    '
Identifikation : 'DVD+-RW ND-6500A'
Revision       : '202C'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Current: 0x0009
Profile: 0x002B 
Profile: 0x001B 
Profile: 0x001A 
Profile: 0x0014 
Profile: 0x0013 
Profile: 0x0011 
Profile: 0x0010 
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
Drive buf size : 1343488 = 1312 KB
FIFO size      : 4194304 = 4096 KB
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data   695 MB        
Total size:      799 MB (79:10.64) = 356298 sectors
Lout start:      799 MB (79:12/48) = 356298 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Is not unrestricted
  Is not erasable
  Disk sub type: Medium Type A, high Beta category (A+) (3)
  ATIP start of lead in:  -11634 (97:26/66)
  ATIP start of lead out: 359846 (79:59/71)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 359846 Blocks current: 359846 Blocks remaining: 3548
Starting to write CD/DVD at speed 24 in real TAO mode for multi session.
Last chance to quit, starting real write in 2 seconds.   1 seconds.   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is ON.
Turning BURN-Free off
Performing OPC...
Starting new track at sector: 0

Track 01:    0 of  695 MB written.
Track 01:    1 of  695 MB written (fifo  89%) [buf  80%]  94.0x.
Track 01:    2 of  695 MB written (fifo 100%) [buf 100%]   2.9x.
Track 01:    3 of  695 MB written (fifo 100%) [buf 100%]  11.9x.
Track 01:    4 of  695 MB written (fifo 100%) [buf 100%]  11.6x.
Track 01:    5 of  695 MB written (fifo 100%) [buf 100%]  12.0x.
Track 01:    6 of  695 MB written (fifo 100%) [buf 100%]  11.6x.
Track 01:    7 of  695 MB written (fifo 100%) [buf 100%]  12.0x.
Track 01:    8 of  695 MB written (fifo 100%) [buf 100%]  11.7x.
Track 01:    9 of  695 MB written (fifo 100%) [buf 100%]  12.0x.
Track 01:   10 of  695 MB written (fifo 100%) [buf 100%]  11.8x.
Track 01:   11 of  695 MB written (fifo 100%) [buf 100%]  12.1x.
Track 01:   12 of  695 MB written (fifo 100%) [buf 100%]  11.8x.
Track 01:   13 of  695 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   14 of  695 MB written (fifo 100%) [buf 100%]  11.8x.
Track 01:   15 of  695 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   16 of  695 MB written (fifo 100%) [buf 100%]  11.9x.
Track 01:   17 of  695 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:   18 of  695 MB written (fifo 100%) [buf 100%]  11.9x.
Track 01:   19 of  695 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:   20 of  695 MB written (fifo 100%) [buf 100%]  11.9x.
Track 01:   21 of  695 MB written (fifo 100%) [buf 100%]  12.3x.
Track 01:   22 of  695 MB written (fifo 100%) [buf 100%]  12.0x.
Track 01:   23 of  695 MB written (fifo 100%) [buf 100%]  12.4x.
Track 01:   24 of  695 MB written (fifo 100%) [buf 100%]  12.0x.
Track 01:   25 of  695 MB written (fifo 100%) [buf 100%]  12.4x.
Track 01:   26 of  695 MB written (fifo 100%) [buf 100%]  12.1x.
Track 01:   27 of  695 MB written (fifo 100%) [buf 100%]  12.5x.
Track 01:   28 of  695 MB written (fifo 100%) [buf 100%]  12.1x.
Track 01:   29 of  695 MB written (fifo 100%) [buf 100%]  12.5x.
Track 01:   30 of  695 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   31 of  695 MB written (fifo 100%) [buf 100%]  12.5x.
Track 01:   32 of  695 MB written (fifo 100%) [buf 100%]  12.2x.
Track 01:   33 of  695 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   34 of  695 MB written (fifo 100%) [buf 100%]  13.0x.
Track 01:   35 of  695 MB written (fifo 100%) [buf 100%]  12.6x.
Track 01:   36 of  695 MB written (fifo 100%) [buf 100%]  13.0x.
Track 01:   37 of  695 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:   38 of  695 MB written (fifo 100%) [buf 100%]  13.1x.
Track 01:   39 of  695 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:   40 of  695 MB written (fifo 100%) [buf 100%]  13.1x.
Track 01:   41 of  695 MB written (fifo 100%) [buf 100%]  12.7x.
Track 01:   42 of  695 MB written (fifo 100%) [buf 100%]  13.2x.
Track 01:   43 of  695 MB written (fifo 100%) [buf 100%]  12.8x.
Track 01:   44 of  695 MB written (fifo 100%) [buf 100%]  13.2x.
Track 01:   45 of  695 MB written (fifo 100%) [buf 100%]  12.8x.
Track 01:   46 of  695 MB written (fifo 100%) [buf 100%]  13.3x.
Track 01:   47 of  695 MB written (fifo 100%) [buf 100%]  12.9x.
Track 01:   48 of  695 MB written (fifo 100%) [buf 100%]  13.3x.
Track 01:   49 of  695 MB written (fifo 100%) [buf 100%]  12.9x.
Track 01:   50 of  695 MB written (fifo 100%) [buf 100%]  13.3x.
Track 01:   51 of  695 MB written (fifo 100%) [buf 100%]  12.9x.
Track 01:   52 of  695 MB written (fifo 100%) [buf 100%]  13.4x.
Track 01:   53 of  695 MB written (fifo 100%) [buf 100%]  13.0x.
Track 01:   54 of  695 MB written (fifo 100%) [buf 100%]  13.4x.
Track 01:   55 of  695 MB written (fifo 100%) [buf 100%]  13.0x.
Track 01:   56 of  695 MB written (fifo 100%) [buf 100%]  13.4x.
Track 01:   57 of  695 MB written (fifo 100%) [buf 100%]  13.1x.
Track 01:   58 of  695 MB written (fifo 100%) [buf 100%]  13.5x.
Track 01:   59 of  695 MB written (fifo 100%) [buf 100%]  13.1x.
Track 01:   60 of  695 MB written (fifo 100%) [buf 100%]  13.5x.
Track 01:   61 of  695 MB written (fifo 100%) [buf 100%]  13.1x.
Track 01:   62 of  695 MB written (fifo 100%) [buf 100%]  13.6x.
Track 01:   63 of  695 MB written (fifo 100%) [buf 100%]  13.0x.
Track 01:   64 of  695 MB written (fifo 100%) [buf 100%]  13.7x.
Track 01:   65 of  695 MB written (fifo 100%) [buf 100%]  14.0x.
Track 01:   66 of  695 MB written (fifo 100%) [buf 100%]  13.6x.
Track 01:   67 of  695 MB written (fifo 100%) [buf 100%]  14.1x.
Track 01:   68 of  695 MB written (fifo 100%) [buf 100%]  13.6x.
Track 01:   69 of  695 MB written (fifo 100%) [buf 100%]  14.1x.
Track 01:   70 of  695 MB written (fifo 100%) [buf 100%]  13.7x.
Track 01:   71 of  695 MB written (fifo 100%) [buf 100%]  14.1x.
Track 01:   72 of  695 MB written (fifo 100%) [buf 100%]  13.7x.
Track 01:   73 of  695 MB written (fifo 100%) [buf 100%]  14.2x.
Track 01:   74 of  695 MB written (fifo 100%) [buf 100%]  13.7x.
Track 01:   75 of  695 MB written (fifo 100%) [buf 100%]  14.2x.
Track 01:   76 of  695 MB written (fifo 100%) [buf 100%]  13.8x.
Track 01:   77 of  695 MB written (fifo 100%) [buf 100%]  14.2x.
Track 01:   78 of  695 MB written (fifo 100%) [buf 100%]  13.8x.
Track 01:   79 of  695 MB written (fifo 100%) [buf 100%]  14.3x.
Track 01:   80 of  695 MB written (fifo 100%) [buf 100%]  13.8x.
Track 01:   81 of  695 MB written (fifo 100%) [buf 100%]  14.3x.
Track 01:   82 of  695 MB written (fifo 100%) [buf 100%]  13.8x.
Track 01:   83 of  695 MB written (fifo 100%) [buf 100%]  14.4x.
Track 01:   84 of  695 MB written (fifo 100%) [buf 100%]  13.9x.
Track 01:   85 of  695 MB written (fifo 100%) [buf 100%]  14.4x.
Track 01:   86 of  695 MB written (fifo 100%) [buf 100%]  13.9x.
Track 01:   87 of  695 MB written (fifo 100%) [buf 100%]  14.4x.
Track 01:   88 of  695 MB written (fifo 100%) [buf 100%]  14.0x.
Track 01:   89 of  695 MB written (fifo 100%) [buf 100%]  14.4x.
Track 01:   90 of  695 MB written (fifo 100%) [buf 100%]  14.0x.
Track 01:   91 of  695 MB written (fifo 100%) [buf 100%]  14.5x.
Track 01:   92 of  695 MB written (fifo 100%) [buf 100%]  14.0x.
Track 01:   93 of  695 MB written (fifo 100%) [buf 100%]  14.5x.
Track 01:   94 of  695 MB written (fifo 100%) [buf 100%]  14.1x.
Track 01:   95 of  695 MB written (fifo 100%) [buf 100%]  14.5x.
Track 01:   96 of  695 MB written (fifo 100%) [buf 100%]  15.0x.
Track 01:   97 of  695 MB written (fifo 100%) [buf 100%]  14.5x.
Track 01:   98 of  695 MB written (fifo 100%) [buf 100%]  15.0x.
Track 01:   99 of  695 MB written (fifo 100%) [buf 100%]  14.5x.
Track 01:  100 of  695 MB written (fifo 100%) [buf 100%]  15.0x.
Track 01:  101 of  695 MB written (fifo 100%) [buf 100%]  14.6x.
Track 01:  102 of  695 MB written (fifo 100%) [buf 100%]  15.1x.
Track 01:  103 of  695 MB written (fifo 100%) [buf 100%]  14.6x.
Track 01:  104 of  695 MB written (fifo 100%) [buf 100%]  15.1x.
Track 01:  105 of  695 MB written (fifo 100%) [buf 100%]  14.6x.
Track 01:  106 of  695 MB written (fifo 100%) [buf 100%]  15.1x.
Track 01:  107 of  695 MB written (fifo 100%) [buf 100%]  14.7x.
Track 01:  108 of  695 MB written (fifo 100%) [buf 100%]  15.1x.
Track 01:  109 of  695 MB written (fifo 100%) [buf 100%]  14.6x.
Track 01:  110 of  695 MB written (fifo 100%) [buf 100%]  15.3x.
Track 01:  111 of  695 MB written (fifo 100%) [buf 100%]  14.7x.
Track 01:  112 of  695 MB written (fifo 100%) [buf 100%]  15.2x.
Track 01:  113 of  695 MB written (fifo 100%) [buf 100%]  14.7x.
Track 01:  114 of  695 MB written (fifo 100%) [buf 100%]  15.2x.
Track 01:  115 of  695 MB written (fifo 100%) [buf 100%]  14.8x.
Track 01:  116 of  695 MB written (fifo 100%) [buf 100%]  15.3x.
Track 01:  117 of  695 MB written (fifo 100%) [buf 100%]  14.8x.
Track 01:  118 of  695 MB written (fifo 100%) [buf 100%]  15.3x.
Track 01:  119 of  695 MB written (fifo 100%) [buf 100%]  14.8x.
Track 01:  120 of  695 MB written (fifo 100%) [buf 100%]  15.3x.
Track 01:  121 of  695 MB written (fifo 100%) [buf 100%]  14.8x.
Track 01:  122 of  695 MB written (fifo 100%) [buf 100%]  15.4x.
Track 01:  123 of  695 MB written (fifo 100%) [buf 100%]  14.9x.
Track 01:  124 of  695 MB written (fifo 100%) [buf 100%]  15.4x.
Track 01:  125 of  695 MB written (fifo 100%) [buf 100%]  14.9x.
Track 01:  126 of  695 MB written (fifo 100%) [buf 100%]  15.3x.
Track 01:  127 of  695 MB written (fifo 100%) [buf 100%]  15.9x.
Track 01:  128 of  695 MB written (fifo  95%) [buf  98%]  14.4x.
Track 01:  129 of  695 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:  130 of  695 MB written (fifo 100%) [buf 100%]  15.4x.
Track 01:  131 of  695 MB written (fifo 100%) [buf 100%]  15.9x.
Track 01:  132 of  695 MB written (fifo 100%) [buf 100%]  15.4x.
Track 01:  133 of  695 MB written (fifo 100%) [buf 100%]  15.9x.
Track 01:  134 of  695 MB written (fifo 100%) [buf 100%]  15.4x.
Track 01:  135 of  695 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:  136 of  695 MB written (fifo 100%) [buf 100%]  15.5x.
Track 01:  137 of  695 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:  138 of  695 MB written (fifo 100%) [buf 100%]  15.5x.
Track 01:  139 of  695 MB written (fifo  98%) [buf  47%]   9.1x.
Track 01:  140 of  695 MB written (fifo 100%) [buf 100%]  53.5x.
Track 01:  141 of  695 MB written (fifo 100%) [buf 100%]  16.0x.
Track 01:  142 of  695 MB written (fifo 100%) [buf  76%]  11.5x.
Track 01:  143 of  695 MB written (fifo 100%) [buf 100%]  25.7x.
Track 01:  144 of  695 MB written (fifo 100%) [buf 100%]  15.6x.
Track 01:  145 of  695 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  146 of  695 MB written (fifo 100%) [buf 100%]  15.6x.
Track 01:  147 of  695 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  148 of  695 MB written (fifo 100%) [buf 100%]  15.6x.
Track 01:  149 of  695 MB written (fifo 100%) [buf 100%]  16.1x.
Track 01:  150 of  695 MB written (fifo 100%) [buf 100%]  15.1x.
Track 01:  151 of  695 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  152 of  695 MB written (fifo 100%) [buf 100%]  15.6x.
Track 01:  153 of  695 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  154 of  695 MB written (fifo  95%) [buf  33%]   8.3x.
Track 01:  155 of  695 MB written (fifo  89%) [buf  98%] 116.1x.
Track 01:  156 of  695 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  157 of  695 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  158 of  695 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  159 of  695 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  160 of  695 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  161 of  695 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  162 of  695 MB written (fifo 100%) [buf 100%]  16.7x.
Track 01:  163 of  695 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  164 of  695 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  165 of  695 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  166 of  695 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  167 of  695 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  168 of  695 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  169 of  695 MB written (fifo 100%) [buf 100%]  16.2x.
Track 01:  170 of  695 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  171 of  695 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  172 of  695 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  173 of  695 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  174 of  695 MB written (fifo 100%) [buf 100%]  16.8x.
Track 01:  175 of  695 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  176 of  695 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  177 of  695 MB written (fifo 100%) [buf 100%]  16.3x.
Track 01:  178 of  695 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  179 of  695 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  180 of  695 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  181 of  695 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  182 of  695 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  183 of  695 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  184 of  695 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  185 of  695 MB written (fifo  92%) [buf  94%]  14.5x.
Track 01:  186 of  695 MB written (fifo 100%) [buf 100%]  19.7x.
Track 01:  187 of  695 MB written (fifo 100%) [buf 100%]  16.4x.
Track 01:  188 of  695 MB written (fifo 100%) [buf 100%]   6.1x.
Track 01:  189 of  695 MB written (fifo  93%) [buf  66%]  11.7x.
Track 01:  190 of  695 MB written (fifo 100%) [buf 100%]  31.8x.
Track 01:  191 of  695 MB written (fifo 100%) [buf 100%]  17.5x.
Track 01:  192 of  695 MB written (fifo  90%) [buf 100%]  16.2x.
Track 01:  193 of  695 MB written (fifo  89%) [buf  54%]  10.9x.
Track 01:  194 of  695 MB written (fifo 100%) [buf 100%]  45.1x.
Track 01:  195 of  695 MB written (fifo 100%) [buf 100%]  17.5x.
Track 01:  196 of  695 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  197 of  695 MB written (fifo 100%) [buf 100%]  17.6x.
Track 01:  198 of  695 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  199 of  695 MB written (fifo 100%) [buf 100%]  17.6x.
Track 01:  200 of  695 MB written (fifo 100%) [buf 100%]  17.0x.
Track 01:  201 of  695 MB written (fifo 100%) [buf 100%]  17.6x.
Track 01:  202 of  695 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:  203 of  695 MB written (fifo 100%) [buf 100%]  17.6x.
Track 01:  204 of  695 MB written (fifo 100%) [buf 100%]  16.9x.
Track 01:  205 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  206 of  695 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:  207 of  695 MB written (fifo 100%) [buf 100%]  17.6x.
Track 01:  208 of  695 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:  209 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  210 of  695 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:  211 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  212 of  695 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:  213 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  214 of  695 MB written (fifo 100%) [buf 100%]  17.1x.
Track 01:  215 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  216 of  695 MB written (fifo 100%) [buf 100%]  17.2x.
Track 01:  217 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  218 of  695 MB written (fifo 100%) [buf 100%]  17.2x.
Track 01:  219 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  220 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  221 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  222 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  223 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  224 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  225 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  226 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  227 of  695 MB written (fifo 100%) [buf 100%]  17.7x.
Track 01:  228 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  229 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  230 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  231 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  232 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  233 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  234 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  235 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  236 of  695 MB written (fifo 100%) [buf 100%]  18.4x.
Track 01:  237 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  238 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  239 of  695 MB written (fifo 100%) [buf 100%]  17.9x.
Track 01:  240 of  695 MB written (fifo 100%) [buf 100%]  18.4x.
Track 01:  241 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  242 of  695 MB written (fifo 100%) [buf 100%]  18.4x.
Track 01:  243 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  244 of  695 MB written (fifo 100%) [buf 100%]  18.4x.
Track 01:  245 of  695 MB written (fifo 100%) [buf 100%]  17.8x.
Track 01:  246 of  695 MB written (fifo 100%) [buf 100%]  18.4x.
Track 01:  247 of  695 MB written (fifo 100%) [buf 100%]  17.9x.
Track 01:  248 of  695 MB written (fifo 100%) [buf 100%]  18.4x.
Track 01:  249 of  695 MB written (fifo 100%) [buf 100%]  17.9x.
Track 01:  250 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  251 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  252 of  695 MB written (fifo 100%) [buf 100%]  18.4x.
Track 01:  253 of  695 MB written (fifo 100%) [buf 100%]  19.0x.
Track 01:  254 of  695 MB written (fifo  98%) [buf  19%]   9.0x.
Track 01:  255 of  695 MB written (fifo  96%) [buf  83%] 120.0x.
Track 01:  256 of  695 MB written (fifo 100%) [buf 100%]  25.0x.
Track 01:  257 of  695 MB written (fifo 100%) [buf 100%]  19.0x.
Track 01:  258 of  695 MB written (fifo 100%) [buf 100%]  18.3x.
Track 01:  259 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  260 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  261 of  695 MB written (fifo 100%) [buf 100%]  19.0x.
Track 01:  262 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  263 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  264 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  265 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  266 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  267 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  268 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  269 of  695 MB written (fifo 100%) [buf 100%]  19.0x.
Track 01:  270 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  271 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  272 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  273 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  274 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  275 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  276 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  277 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  278 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  279 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  280 of  695 MB written (fifo 100%) [buf 100%]  18.5x.
Track 01:  281 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  282 of  695 MB written (fifo 100%) [buf 100%]  19.7x.
Track 01:  283 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  284 of  695 MB written (fifo 100%) [buf 100%]  19.7x.
Track 01:  285 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  286 of  695 MB written (fifo  98%) [buf 100%]  19.7x.
Track 01:  287 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  288 of  695 MB written (fifo  90%) [buf  64%]  12.9x.
Track 01:  289 of  695 MB written (fifo 100%) [buf 100%]  38.3x.
Track 01:  290 of  695 MB written (fifo 100%) [buf 100%]  19.7x.
Track 01:  291 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  292 of  695 MB written (fifo 100%) [buf 100%]  19.8x.
Track 01:  293 of  695 MB written (fifo  96%) [buf 100%]  18.2x.
Track 01:  294 of  695 MB written (fifo 100%) [buf 100%]  20.8x.
Track 01:  295 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  296 of  695 MB written (fifo 100%) [buf 100%]  19.7x.
Track 01:  297 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  298 of  695 MB written (fifo 100%) [buf 100%]  19.7x.
Track 01:  299 of  695 MB written (fifo 100%) [buf 100%]  19.1x.
Track 01:  300 of  695 MB written (fifo 100%) [buf 100%]  19.7x.
Track 01:  301 of  695 MB written (fifo 100%) [buf 100%]  19.2x.
Track 01:  302 of  695 MB written (fifo 100%) [buf 100%]  19.5x.
Track 01:  303 of  695 MB written (fifo  93%) [buf  82%]  15.2x.
Track 01:  304 of  695 MB written (fifo 100%) [buf 100%]  27.6x.
Track 01:  305 of  695 MB written (fifo 100%) [buf 100%]  19.1x.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 02 63 C4 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 40s
cdrecord: The current problem looks like a buffer underrun.
cdrecord: Try to use 'driveropts=burnfree'.
cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.

write track data: error after 320741376 bytes
Writing  time:  151.420s
Average write speed  32.1x.
Min drive buffer fill was 19%
Fixating...
Fixating time:   34.236s
cdrecord: fifo had 5116 puts and 5053 gets.
cdrecord: fifo was 0 times empty and 4757 times full, min fill was 81%.

```

---

### Post by Pig Monkey on 2005-08-19
I get the same gnomebaker error. Anybody know? I've tried burning at slow speeds (4x) and running as root. Nothing seems to help.

---

