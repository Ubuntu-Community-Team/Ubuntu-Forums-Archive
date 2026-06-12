---
title: "1420 disk issues"
date: 2007-10-04
forum: Dell  Ubuntu Support
---

### Post by alexb2 on 2007-10-04
I have an Inspiron 1420 with Dell's Ubuntu install plus all the latest Feisty updates. I got my first "25 mounts now you need to fsck" today and noticed much output similar to the following:

```
[   33.664000] ata1.00: exception Emask 0x2 SAct 0x4 SErr 0x0 action 0x2 frozen
[   33.664000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x4 FIS=004040a1:00000002)
[   33.664000] ata1.00: cmd 60/18:10:49:3e:7a/00:00:01:00:00/40 tag 2 cdb 0x0 data 12288 in
[   33.664000]          res 40/00:10:49:3e:7a/00:00:01:00:00/40 Emask 0x2 (HSM violation)
[   33.976000] ata1: soft resetting port
[   34.148000] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   34.148000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   34.148000] ata1.00: ata_hpa_resize 1: sectors = 312581808, hpa_sectors = 312581808
[   34.148000] ata1.00: configured for UDMA/133
[   34.148000] ata1: EH complete
[   34.148000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[   34.148000] sda: Write Protect is off
[   34.148000] sda: Mode Sense: 00 3a 00 00
[   34.148000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
```

Before each instance where this was printed on the screen the progress bar for fsck would first slow down and then come to a stop.  After the message it would eventually speed up again until it hit another problem spot.

I've attached output from dmesg and lspci -vvv - sorry about the gzipping but the forum didn't like the size of the raw txt.  Here's uname -a:

Linux entropy 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux



If anybody has any idea as to what's going on and whether or not this indicates an impending disk failure I'd be much obliged.  Dell's response was "Call this number for Ubuntu support!" which then gave me a friendly message stating that there is no Ubuntu support.  Is there a trick to get bumped up a tier or two on the support ladder and get someone who isn't reading from a script?  A secret code word perhaps?

---

### Post by alexb2 on 2007-10-05
*bump*

---

### Post by xiaoyong on 2007-10-08
Maybe you need to modify the /etc/fstab, so the system won't examine the harddisk when booting every time.  But I don't think it is a good idea.  Or try to change the file system from ext2/3 to xfs/jfs.

---

### Post by alexb2 on 2007-10-08
> **xiaoyong said:**
> Maybe you need to modify the /etc/fstab, so the system won't examine the harddisk when booting every time.  But I don't think it is a good idea.  Or try to change the file system from ext2/3 to xfs/jfs.

This is an error from libata, not a filesystem issue.

Upon further googling it seems that this drive simply needs to be added to libata's NCQ blacklist, which is fine by me since NCQ almost always results in decreased performance for desktop systems.

Does anyone know of a generic kernel boot option to disable NCQ entirely?

---

