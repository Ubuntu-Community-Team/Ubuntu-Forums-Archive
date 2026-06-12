---
title: "Ubuntu &quot;Disks&quot; have upper limit ?"
date: 2021-09-16
forum: Desktop Environments
---

### Post by oden99 on 2021-09-16
I  was playing around with the "Disks" performance test, testing a nvme drive.
The test seems to have a limit of 5540 since all I get on the graph are a blue line at 5540MB.

Doing a speed test from Shell with "sudo hdparm -Tt /dev/e0n1p3" gives the result:
Timing cached reads:   58674 MB in  2.00 seconds = 29406.30 MB/sec
Timing buffered disk reads: 6920 MB in  3.00 seconds = 2306.45 MB/sec

So it seems there is a bug/limitation in the GUI of "Disks" software limiting the output at 5540 MB

Since drives get faster I think it would be a good idea to raise the limit for the output to 10 000 or so (or even higher for future needs)

Ubuntu 20.04.3 LTS gnome-Version 3.36.8 x64

---

### Post by ActionParsnip on 2021-09-16
I suggest you report a bug

---

### Post by TheFu on 2021-09-16
For everyone unfamiliar with what's possible.

> How fast is PCIe NVMe 3.0
    PCIe 3.0 1x : 7.88Gb/s x 125 = 984.6MB/s
    PCIe 3.0 2x : 15.76Gb/s x 125 = 1,970MB/s
    PCIe 3.0 4x : 31.52Gb/s x 125 = 3,940MB/s
    PCIe 3.0 8x : 63.04Gb/s x 125 = 7,880MB/s
    PCIe 3.0 16x : 126.4Gb/s x 125 = 15,800MB/s

How fast is PCIe NVMe 4.0
    PCIe 4.0 1x : 15.76Gb/s x 125 = 1,970MB/s
    PCIe 4.0 2x : 31.52Gb/s x 125 = 3,940MB/s
    PCIe 4.0 4x : 63.04Gb/s x 125 = 7,880MB/s
    PCIe 4.0 8x : 126.4Gb/s x 125 = 15,800MB/s
    PCIe 4.0 16x : 252Gb/s x 125 = 31,500MB/s

My old Ryzen 2xxx is PCIe 3 with NVMe and 4x ... so 31.52Gb/s x 125 = 3,940MB/s is the theoretical max. The specs for a new NVMe SSD here say the Max. 3,500 MB/s, so it is PCIe v3 4x (confirmed on the vendor specifications page).  I really need to get that installed somewhere.

 In the real world, it will be less.  On that machine, I'm using a SATA SSD which gnome-disks says gets **480.6 MB/s** for a 100 sample read test. hdparm -Tt says:
```
 Timing cached reads:   17800 MB in  2.00 seconds = 8909.33 MB/sec
 Timing buffered disk reads: 1290 MB in  3.00 seconds = **429.73 MB/sec**
```

Without knowing how the 2 different tests are actually performed, we really shouldn't attempt to compare results from 2 different programs. In all these tests, the details matter.  Even if the tests were named identically, because 2 different tools are used, that's enough to know their are differences.

---

