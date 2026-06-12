---
title: "&quot;no space left on device&quot; is not true!"
date: 2009-01-17
forum: General Help
---

### Post by kakyoism on 2009-01-17
I was copying data from local harddrive to a mounted USB drive.
when df -h gives me "128G" available on that USB. The cp command complains
that there is "no space left on device"!

Via Nautilus it has the same problem, but only on certain files! Confused.


Help!

---

### Post by dcstar on 2009-01-17
> **kakyoism said:**
> I was copying data from local harddrive to a mounted USB drive.
when df -h gives me "128G" available on that USB. The cp command complains
that there is "no space left on device"!
......

Unmount it and do a **fsck** on the partition.

---

