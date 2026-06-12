---
title: "HDD read errors"
date: 2010-05-11
forum: Desktop Environments
---

### Post by Larsix on 2010-05-11
I could really use some help/advice in recovering data from my Ubuntu 9.04 drive.  I left my work machine on over the weekend and came in Monday morning to find an unresponsive black screen with just a blinking cursor.  I rebooted, it showed the ring of people logo, then would go black and after a minute or so, and load into blackbox with errors all over the place.  

So I booted with a 10.04 LiveCD and I'm having trouble even reading the drive at all.  I try to mount it and it gives this error:
```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```doing "dmesg | tail" returns this:
```
[  243.092397] Descriptor sense data with sense descriptors (in hex):
[  243.092401]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  243.092416]         0e 05 0b 99 
[  243.092422] sd 2:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[  243.092429] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 0e 05 0b 5f 00 01 00 00
[  243.092443] end_request: I/O error, dev sda, sector 235211673
[  243.092470] ata3: EH complete
[  243.092501] JBD: Failed to read block at offset 8556
[  243.092508] JBD: recovery failed
[  243.092511] EXT4-fs (sda1): error loading journal
```and doing fdisk on it returns this:
```
unable to open /dev/sda
```Any ideas on how I could recover files from it?  Or is it a total lost cause?

By the way, it is a P4 dual core 3.0 GHz with 2.5GB RAM and a 250GB HDD (Ext4, Ubuntu 9.04).

---

