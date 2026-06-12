---
title: "CD Writing problems with mini-cd"
date: 2006-03-31
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-03-31
Is anyone experiencing such issues, or know a workaround. 

I am trying to write to a Memorex CD-RW 210MB (mini-cd). I tried graveman, gnomebaker (which always crashes nowadays) and cdrecord. everytime the write completes (without errors) and I try to mount the cd, it says: 
```

wrong fs type blabla
``` and dmesg | tail gives ```

[4298236.984000] ATAPI device hdc:
[4298236.984000]   Error: Medium error -- (Sense key=0x03)
[4298236.984000]   (reserved error code) -- (asc=0x31, ascq=0x00)
[4298236.984000]   The failed "Read Cd/Dvd Capacity" packet command was:
[4298236.984000]   "25 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 "
[4298236.986000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
[4298236.986000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
[4298236.986000] ide: failed opcode was: unknown
[4298236.986000] end_request: I/O error, dev hdc, sector 64
[4298236.986000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16

```

Windows doesn't read this cd either... I will try writing to it in Windows later on, but what do I do about Linux?

**EDIT: Windows was able to erase the disc, write to it, and read what it read. Linux also was able to read data burned in Windows** That's confusing, to me...


---

---

### Post by towsonu2003 on 2006-04-01
I just tried k3b as well. It couldn't do the job either. Windows can burn to this, but Linux can't? :confused: 

+ bump

---

### Post by towsonu2003 on 2006-04-13
filed bug for breezy cdrecord (cdrtools): [https://launchpad.net/distros/ubuntu/+source/cdrtools/+bug/39521](https://launchpad.net/distros/ubuntu/+source/cdrtools/+bug/39521)

---

