---
title: "CD Burn Fails in GnomeBaker"
date: 2005-11-23
forum: Desktop Environments
---

### Post by Scanner on 2005-11-23
I am trying to burn a couple of ISOs using GnomeBaker and I get the following message, and have no idea what it means, any ideas would be appreciated.  It says the write fails in the status window.

Track 01:  484 of  681 MB written (fifo 100%) [buf   0%]   2.3x.cdrecord: Success. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 03 C8 06 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 2.509s timeout 40s
cdrecord: A write error occured.
cdrecord: Please properly read the error message above.

write track data: error after 507523072 bytes
Writing  time:  423.640s
Average write speed  11.0x.
Min drive buffer fill was 0%
Total of 1 possible drive buffer underruns predicted.
Fixating...
Fixating time:   35.788s
cdrecord: fifo had 8058 puts and 7995 gets.
cdrecord: fifo was 0 times empty and 7851 times full, min fill was 93%.

---

### Post by az on 2005-11-23
[QUOTE=Scanner]cdrecord: Please properly read the error message above.
[/QUOTE]

Cdrecord is a rude *sshole.

[QUOTE=Scanner]
Total of 1 possible drive buffer underruns predicted.
[/QUOTE]

That would be the problem.  It seems to be burning at 11x.  What speed did you pick and do you have burnfree on?

---

### Post by Scanner on 2005-11-23
[QUOTE=azz] It seems to be burning at 11x.  What speed did you pick and do you have burnfree on?[/QUOTE]

It should have burned at 8X, and what is burnfree, and where do I get it, I checked the repos including mulitverse?

---

### Post by az on 2005-11-23
Burnfree is a cd burning option.  Just before you burn your cd, you tick the options you want.  If your cd burner supports burnfree (I think if it was made after 2001, it does) you should be able to tick the burnfree box and that will provide a way to avoid buffer underuns.

---

