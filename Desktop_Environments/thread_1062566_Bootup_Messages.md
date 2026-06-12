---
title: "Bootup Messages"
date: 2009-02-07
forum: Desktop Environments
---

### Post by tx836519 on 2009-02-07
I recently had to do a low level format of the hard-disk that boots Ubuntu 8.04 (Hardy Heron).  I made and image of the OS partition using Norton Ghost and backed all other data on the disk.  After the low level format, I repartitioned the disk as before and restored the OS and data to the drive.

The system boots and runs OK, but the boot-up process now generates a series of messages starting with:

Reading files needed to boot ....

Looking at the system log and comparing with other machines running the same OS on similar but different hardware, it looks like the first indication of a problem is:

Feb  6 14:23:22 ken-desktop kernel: [   18.000288] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

How can I re-create this file?  -- ken

---

### Post by Antonio Lo Nardo on 2009-02-08
Read this:
[http://ubuntuforums.org/showthread.php?t=629707](http://ubuntuforums.org/showthread.php?t=629707)

---

