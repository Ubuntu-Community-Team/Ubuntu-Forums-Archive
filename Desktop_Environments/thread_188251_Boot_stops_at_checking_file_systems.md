---
title: "Boot stops at checking file systems"
date: 2006-06-03
forum: Desktop Environments
---

### Post by thecdn on 2006-06-03
I got dapper installed, but when I try to boot I get the following:

It goes through the splash screen, hits 'Checking all filesystems,' and drops to text, ending in.

  *Checking all filesystems...
dosfsck 1.11, 12 Mar 2005, FAT32, LFN
/sda5img.gz.000
  File size is 0 bytes, cluster chain length is > 0 bytes.
  Truncating file to 0 bytes,
  Truncating file to 0 bytes.er chain length is > 0 bytes.

And then it just hangs....

sda5 is the partition on my sata drive that has my pclos root. Ubuntu is on my ide drive all in hdb7.

If I press ctrl-c, then ctrl-d, it will finish booting normally into the desktop. Any ideas of what I need to do to fix this and have a normal boot?

---

