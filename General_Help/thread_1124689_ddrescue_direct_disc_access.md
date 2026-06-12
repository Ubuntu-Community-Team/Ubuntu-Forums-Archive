---
title: "ddrescue direct disc access"
date: 2009-04-13
forum: General Help
---

### Post by osx on 2009-04-13
I'm using ddrescue to recover data from a failing hard drive. In the ddrescue info documentation it says:

> 6 Direct Disc Access
********************

If you notice that the sizes and offsets in the log file are ALWAYS
multiples of the hardware block size, maybe your kernel is caching the
disc accesses and grouping them. In this case you may want to use direct
disc access or a raw device to bypass the kernel cache and rescue more
of your data.

   NOTE! Hardware block size must be correctly set with the
`--block-size' option for this to work. Try the `--direct' option
first. If direct disc access is not available in your system, try raw
devices. Read your system documentation to find how to bind a raw
device to a regular block device.

The question I have is in regards to the information next to the "NOTE" which says "If direct disc access is not available in your system...". I assume kernel caching reads/grabs multiple sectors at once in "chunks" so that drives with a certain number of sectors resulting in an incomplete "chunk" at the end of the recovery would not be captured (i.e., if a chunk is 4 sectors and there are 3 remaining sectors at the end of your drive, those last 3 sectors would be skipped because they don't fill a chunk). If my understanding is correct, direct disc access disables kernel caching for accessing the source drive and results in a sector-for-sector/block-for-block copy so that every sector is copied.

How can I tell if Ubuntu allows "direct disc access"? Is it something compiled into the kernel? Is there a command to tell?

I want to make sure I am recovering all the data I possibly can.

Thanks.

---

