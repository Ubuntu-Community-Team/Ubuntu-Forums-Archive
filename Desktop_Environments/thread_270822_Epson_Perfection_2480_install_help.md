---
title: "Epson Perfection 2480 install help"
date: 2006-10-03
forum: Desktop Environments
---

### Post by kpictjl on 2006-10-03
I feel like I've tried everything.  I can't make my Epson Perfection 2480 Photo flatbed scanner work.  The tools lsusb and sane-find-scanner seem to be able to find the scanner.  Scanimage does not find it (see output below).  xsane v.097 returns the "no devices available" dialog box.  I'm useing this firmware, esfw41.bin, and my snapscan.conf file points to it.  I'm running dapper drake and have reinstalled every scanner and sane application that I can think of.

Help!

```
bighead@jimsoldgw2k:/usr/share/sane/snapscan$ lsusb
Bus 001 Device 009: ID 1058:0701 Western Digital Technologies, Inc.
Bus 001 Device 008: ID 04b8:0121 Seiko Epson Corp.
Bus 001 Device 001: ID 0000:0000
bighead@jimsoldgw2k:/usr/share/sane/snapscan$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x0121) at libusb:001:008
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
bighead@jimsoldgw2k:/usr/share/sane/snapscan$ sudo scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
bighead@jimsoldgw2k:/usr/share/sane/snapscan$
```

---

### Post by kpictjl on 2006-12-14
I think it's fixed, see this thread for more information...
[http://ubuntuforums.org/showthread.php?t=143504&page=2](http://ubuntuforums.org/showthread.php?t=143504&page=2)

---

