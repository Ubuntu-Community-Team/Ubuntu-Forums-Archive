---
title: "unable to copy vcd"
date: 2006-04-15
forum: Desktop Environments
---

### Post by manish_m on 2006-04-15
hi
i have a odd problem with my system. when i insert a vcd, totem runs and plays it.
but when i try to copy the cd it gives i/o error.
dmesg gives the following output:
[4295648.034000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4295648.034000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4295648.034000] ide: failed opcode was: unknown
[4295648.034000] end_request: I/O error, dev hdc, sector 0
[4295648.034000] printk: 1 messages suppressed.
[4295648.034000] Buffer I/O error on device hdc, logical block 0
[4295648.037000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4295648.037000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4295648.037000] ide: failed opcode was: unknown
[4295648.037000] end_request: I/O error, dev hdc, sector 4
[4295648.037000] Buffer I/O error on device hdc, logical block 1
[4295648.040000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4295648.040000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4295648.040000] ide: failed opcode was: unknown
[4295648.040000] end_request: I/O error, dev hdc, sector 8
[4295648.040000] Buffer I/O error on device hdc, logical block 2
[4295648.043000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
i have even tried dd, it doesn't work.
Can anybody help me.

---

