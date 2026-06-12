---
title: "efax inability to send fax"
date: 2010-06-14
forum: Desktop Environments
---

### Post by chinna saaeb on 2010-06-14
When I try to send fax the following mesagge crops

 fax send 2311505 output.ps
output.ps.nnn is up-to-date
efax: Mon Jun 14 17:42:37 2010 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 42:37 Error: can't read multi-strip TIFF files
efax: 42:37 Error: missing offset to TIFF data
efax: 42:37 done, returning 2 (unrecoverable error)
There were errors (see T2311505.efax.log)

The logfile is as follows:

efax: Mon Jun 14 17:53:44 2010 efax v 0.9a-001114 Copyright 1999 Ed Casas
efax: 53:44 compiled Jun 21 2006 05:59:09
efax: 53:44 TIFF version 4.2 file (little-endian)
efax: 53:44 TIFF directory at 26840 with 20 tagscan't read multi-strip TIFF files
efax: 53:44 Error: missing offset to TIFF data
efax: 53:44 argv[0]=efax
efax: 53:44 argv[1]=-v
efax: 53:44 argv[2]=ewin
efax: 53:44 argv[3]=-v
efax: 53:44 argv[4]=chewmainrxtf
efax: 53:44 argv[5]=-d/dev/ttyS0
efax: 53:44 argv[6]=-x
efax: 53:44 argv[7]=/var/lock/LCK..ttyS0
efax: 53:44 argv[8]=-iZ
efax: 53:44 argv[9]=-i&FE&D2S7=120
efax: 53:44 argv[10]=-i&C0
efax: 53:44 argv[11]=-iM1L0
efax: 53:44 argv[12]=-l
efax: 53:44 argv[13]=+1 800 555 5555
efax: 53:44 argv[14]=-kZ
efax: 53:44 argv[15]=-h
efax: 53:44 argv[16]=2010/06/14 17:53 +1 800 555 5555 asd p. %d/%d
efax: 53:44 argv[17]=-t
efax: 53:44 argv[18]=T44311505
efax: 53:44 argv[19]=output.ps.001
efax: 53:44 done, returning 2 (unrecoverable error)

I am using ubuntu 10.04 LTS i386

---

### Post by Scunizi on 2010-06-22
I'm having the same issue.. use to work fine in previous releases.  As per other forum posts I've tried modifying the GS line in /usr/bin/fax but that didn't seem to fix it either.. 

For those of us still REQUIRED to fax documents hither and yon, it is imperative we find a fix.

---

