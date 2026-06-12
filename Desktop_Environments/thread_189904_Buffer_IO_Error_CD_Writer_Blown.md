---
title: "Buffer I/O Error CD Writer: Blown?"
date: 2006-06-05
forum: Desktop Environments
---

### Post by aquaboot on 2006-06-05
Hi All,

hdc is my cd writer which will not open. I get the following lengthy mesg. via dmesg (sorry for the length):

What the heck is going on? Thanks, ab

#############################################################################################

hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294697.414000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294697.414000] ide: failed opcode was: unknown
[4294697.414000] end_request: I/O error, dev hdc, sector 0
[4294697.414000] Buffer I/O error on device hdc, logical block 0
[4294699.216000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294699.216000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294699.216000] ide: failed opcode was: unknown
[4294699.216000] end_request: I/O error, dev hdc, sector 8
[4294699.216000] Buffer I/O error on device hdc, logical block 1
[4294701.018000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294701.018000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294701.018000] ide: failed opcode was: unknown
[4294701.018000] end_request: I/O error, dev hdc, sector 16
[4294701.018000] Buffer I/O error on device hdc, logical block 2
[4294702.820000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294702.820000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294702.820000] ide: failed opcode was: unknown
[4294702.820000] end_request: I/O error, dev hdc, sector 24
[4294702.820000] Buffer I/O error on device hdc, logical block 3
[4294704.622000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294704.622000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294704.622000] ide: failed opcode was: unknown
[4294704.622000] end_request: I/O error, dev hdc, sector 32
[4294704.622000] Buffer I/O error on device hdc, logical block 4
[4294706.424000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294706.424000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294706.424000] ide: failed opcode was: unknown
[4294706.424000] end_request: I/O error, dev hdc, sector 40
[4294706.424000] Buffer I/O error on device hdc, logical block 5
[4294708.226000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294708.226000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294708.226000] ide: failed opcode was: unknown
[4294708.226000] end_request: I/O error, dev hdc, sector 48
[4294708.226000] Buffer I/O error on device hdc, logical block 6
[4294710.028000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294710.028000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294710.028000] ide: failed opcode was: unknown
[4294710.028000] end_request: I/O error, dev hdc, sector 56
[4294710.028000] Buffer I/O error on device hdc, logical block 7
[4294711.830000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294711.830000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294711.830000] ide: failed opcode was: unknown
[4294711.830000] end_request: I/O error, dev hdc, sector 0
[4294711.830000] Buffer I/O error on device hdc, logical block 0
[4294716.877000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294716.877000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294716.877000] ide: failed opcode was: unknown
[4294716.877000] end_request: I/O error, dev hdc, sector 1429504
[4294722.382000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294722.382000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294722.382000] ide: failed opcode was: unknown
[4294722.382000] end_request: I/O error, dev hdc, sector 0
[4294724.424000] hdc: command error: status=0x51 { DriveReady SeekComplete Error }
[4294724.424000] hdc: command error: error=0x54 { AbortedCommand LastFailedSense=0x05 }
[4294724.424000] ide: failed opcode was: unknown
[4294724.424000] end_request: I/O error, dev hdc, sector 0
[4294724.657000] cdrom: open failed.

---

### Post by aquaboot on 2006-06-05
Not sure what happened, but I've fixed it.  I rebooted and just after BIOS, opened the cd drive (shows it was an os issue).  I held it open all through the dapper boot up and presto, no error messages. Once in the os, I can now open and close the cdr with no problem.  I'd still like to know what happened though.  Any Ideas?

Relieved,

ab

---

