---
title: "usb harddrive doesnt works anymore"
date: 2007-06-22
forum: Dell  Ubuntu Support
---

### Post by tompouce on 2007-06-22
Hey there!

I was always using my extern usb harddrive because my music and stuff are on this.

But now it doesnt works anymore on linux (on windows yeah) I get this from dmesg:
```

[  254.284000] usb-storage: device found at 6
[  254.284000] usb-storage: waiting for device to settle before scanning
[  259.284000] usb-storage: device scan complete
[  259.288000] scsi 3:0:0:0: Direct-Access     WDC WD25 00JB-00GVC0      0811 PQ: 0 ANSI: 0
[  259.304000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[  259.308000] sdb: test WP failed, assume Write Enabled
[  259.308000] sdb: assuming drive cache: write through
[  259.312000] SCSI device sdb: 488397168 512-byte hdwr sectors (250059 MB)
[  259.312000] sdb: test WP failed, assume Write Enabled
[  259.312000] sdb: assuming drive cache: write through
[  259.312000]  sdb: sdb1
[  259.320000] sd 3:0:0:0: Attached scsi disk sdb
[  259.320000] sd 3:0:0:0: Attached scsi generic sg2 type 0

```

So I am wondering, is it supposed to be there? weird... It's not mounted anymore...

EDIT: I think it's since I installed Beagle... :S

Thanks!

---

### Post by trak87 on 2007-06-22
I'd boot up with a knoppix live cd, plug in the usb disk and test it there just in case something is screwy in Ubuntu. You might also try manually mounting the drive and see if you can get your data off before things get worse.

---

