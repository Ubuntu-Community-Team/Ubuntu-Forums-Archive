---
title: "CanonScan Lide25"
date: 2006-05-29
forum: Desktop Environments
---

### Post by mparker on 2006-05-29
I've got BreezyBadger 5.10 and I can't get sane to recognize my scanner.. A canon lide25.
When running
sudo sane-find-scanner
I get output below indicating it finds the usb scanner, but I can't figure how to get it to run because when I run scanimage -L it tells me there is no scanning devices...??

Anyone got any ideas where i've gone wrong?

Thanks in advance.
Myles

# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x067b, product=0x2303) at libusb:004:004
found USB scanner (vendor=0x04a9 [Canon], product=0x2220 [CanoScan], chip=LM9832/3) at libusb:001:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

---

