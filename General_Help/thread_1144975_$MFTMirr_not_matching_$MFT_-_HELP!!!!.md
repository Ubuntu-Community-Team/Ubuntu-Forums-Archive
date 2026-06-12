---
title: "$MFTMirr not matching $MFT - HELP!!!!"
date: 2009-05-01
forum: General Help
---

### Post by 00Davo on 2009-05-01
I'm trying to mount my Windows NTFS installation with Ubuntu 8.10 - the NTFS partition is on /dev/sdb1. It gives the error in the title: "$MFTMirr not matching $MFT" whenever I attempt to mount. This has occurred previously, but was easily solved, using the ntfsfix command from ntfsprogs.

Trying ntfsfix now, however, only gives the following output:
> Mounting volume... $MFTMirr location mismatch or first 4 records are fragmented. Run chkdsk.
Failed to load $MFTMirr: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... $MFTMirr location mismatch or first 4 records are fragmented. Run chkdsk.
Failed to load $MFTMirr: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.

Additionally, the Windows installation on the partition in question isn't appearing in my GRUB menu, so I can't boot into it for access to chkdsk. What do I do?

---

