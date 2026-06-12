---
title: "Is scanning with the HP CM1312 MFP supported under Ubuntu / Linux?"
date: 2009-04-02
forum: General Help
---

### Post by nemarona on 2009-04-02
Hi all.

I've run into trouble trying to scan with the HP CM1312nfi MFP under both Ubuntu and Kubuntu 8.10 with all the latest updates. Printing works beautifully with both boxes, but the scanning portion of the MFP seems not to be detected by sane.

Any ideas?
Thanks in advance!

---

### Post by nemarona on 2009-04-02
Here's the output to a couple of (hopefully relevant) commands:
```
scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
```

```
sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x03f0 [Hewlett-Packard], product=0x4f17 [HP Color LaserJet CM1312nfi MFP]) at libusb:001:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
```

---

