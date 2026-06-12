---
title: "Kernel does not use FS cache? (44% free memory)"
date: 2006-09-26
forum: Desktop Environments
---

### Post by ps- on 2006-09-26
Hello,

on my T60p notebook, the kernel does not use the whole memory to cache his filesystem operations:

> 
MemTotal:      2072836 kB
MemFree:        922640 kB
Buffers:           572 kB
Cached:         566684 kB
SwapCached:          0 kB
Active:         698684 kB
Inactive:       334376 kB
HighTotal:     1178432 kB
HighFree:       208616 kB
LowTotal:       894404 kB
LowFree:        714024 kB
SwapTotal:     3951980 kB
SwapFree:      3951980 kB
Dirty:             168 kB
Writeback:           0 kB
Mapped:         631900 kB
Slab:            84704 kB
CommitLimit:   4988396 kB
Committed_AS:   962076 kB
PageTables:       3172 kB
VmallocTotal:   114680 kB
VmallocUsed:     13688 kB
VmallocChunk:   100548 kB


shouldnt it use more memory? applications and cache does make ~50% of ram. the other 50% are free.

I just upgraded from 1GB to 2GB - is it possible that the information of 1GB is saved somewhere?

maybe its important: I activated laptop-mode .. dont know if this makes any difference.

thanks in advance, 
piero

---

### Post by kidders on 2006-09-26
Hi there,

Have you any reason to believe that your system *should* be using all your RAM? Why did you add the extra gigabyte?

The straight answer to your question is no... it's not possible.

Hope that helps :-)

---

