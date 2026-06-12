---
title: "SATA DVD drive not detected in Jaunty"
date: 2009-04-24
forum: Desktop Environments
---

### Post by gtdaqua on 2009-04-24
Ever since testing Jaunty on my Dell Optiplex 740, the SATA DVD drive is not detected. 

Updated the Dell BIOS and issue persists. I reported a bug last month and still no updates!

[Ubuntu Kernel Bug - https://bugs.launchpad.net/ubuntu/+bug/344093](https://bugs.launchpad.net/ubuntu/+bug/344093)

```

**[    3.420194] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1A, max UDMA/33**
[    3.420204] ata2.00: applying bridge limits
[    3.452207] ata2.00: configured for UDMA/33
[    8.452027] ata2.00: qc timeout (cmd 0xa0)
[    8.452031] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[    9.332040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    9.388205] ata2.00: configured for UDMA/33
[   14.388025] ata2.00: qc timeout (cmd 0xa0)
[   14.388029] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[   14.388031] ata2: limiting SATA link speed to 1.5 Gbps
[   14.388034] ata2.00: limiting speed to UDMA/33:PIO3
[   15.268040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   15.324206] ata2.00: configured for UDMA/33
[   20.324023] ata2.00: qc timeout (cmd 0xa0)
[   20.324027] ata2.00: TEST_UNIT_READY failed (err_mask=0x5)
[   20.324029] ata2.00: disabled
[   20.324041] ata2: hard resetting link
[   21.204040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)

```

I am running Kernel 2.6.28-11-generic

---

### Post by gtdaqua on 2009-05-15
Can anybody help? I am still having this issue.

---

### Post by gtdaqua on 2009-08-17
I installed Ubuntu Karmic Alpha 4 and the SATA DVD drive was detected without any problems!

I am happy that I can move away from Hardy 8.04. Back on the bleeding-edge distro!

Kernel:
```

Linux trust 2.6.31-5-generic #24-Ubuntu SMP Sat Aug 1 12:48:18 UTC 2009 i686 GNU/Linux

```

dmesg.log file attached. The output related to SATA DVD in the dmesg is here (no errors reported relating to SATA DVD)

```

[ 1.283789] Using IPI No-Shortcut mode
[ 1.283969] PM: Resume from disk failed.
[ 1.283984] registered taskstats version 1
[ 1.284133] Magic number: 5:777:11
[ 1.284145] misc pktcdvd!control: hash matches
[ 1.284251] rtc_cmos 00:04: setting system clock to 2009-08-17 05:02:10 UTC (1250485330)
[ 1.284255] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.284257] EDD information not available.
[ 1.286967] sda5 sda6 sda7 >
[ 1.314515] sd 0:0:0:0: [sda] Attached SCSI disk
[B][ 1.380044] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 1.412199] ata2.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1C, max UDMA/33
[ 1.412209] ata2.00: applying bridge limits
[ 1.452208] ata2.00: configured for UDMA/33
[ 1.456104] scsi 1:0:0:0: CD-ROM PBDS DVD+-RW DS-8W1P BD1C PQ: 0 ANSI: 5
[ 1.467147] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[ 1.467150] Uniform CD-ROM driver Revision: 3.20
[ 1.467314] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 1.467448] sr 1:0:0:0: Attached scsi generic sg1 type 5[/B]
[ 1.477931] ata4: SATA link down (SStatus 0 SControl 300)
[ 1.477964] Freeing unused kernel memory: 536k freed
[ 1.478361] Write protecting the kernel text: 4548k
[ 1.478397] Write protecting the kernel read-only data: 1828k
[ 1.564212] Linux agpgart interface v0.103
[ 1.587584] [drm] Initialized drm 1.1.0 20060810
[ 1.693018] usb 2-4: new full speed USB device using ohci_hcd and address 2
[ 1.898126] tg3.c:v3.99 (April 20, 2009)
[ 1.898519] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16

```
Hope the 2.6.31 and higher kernels keeps this drive alive.

---

