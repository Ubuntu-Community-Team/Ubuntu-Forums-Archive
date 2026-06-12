---
title: "can't mount SSD, many error msgs"
date: 2010-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by inspiron910 on 2010-11-15
Can boot Inspiron 910 from Ubuntu USB flash boot drive but can't access SSD:

Cannot mount volume

mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or helper program, or other error

It goes on to suggest syslog -try and so, neither of which works as a terminal command. Also suggests dmesg | tail which returns

[24386.114909] lost page write due to I/O error on sda
[24386.114980] ata1: EH complete
[24386.124543] sd 0:0:0:0: [sda] 120378384 512-byte hardware sectors: (61.6 GB/57.4 GiB)
[24386.125258] sd 0:0:0:0: [sda] Write Protect is off
[24386.125276] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[24386.127928] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[24386.129079] sd 0:0:0:0: [sda] 120378384 512-byte hardware sectors: (61.6 GB/57.4 GiB)
[24386.129649] sd 0:0:0:0: [sda] Write Protect is off
[24386.129668] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[24386.134501] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA


Any suggestions? Thanks.

---

