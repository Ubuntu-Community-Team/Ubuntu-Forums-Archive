---
title: "Backup with rsync"
date: 2006-02-16
forum: Desktop Environments
---

### Post by Maelgwyn on 2006-02-16
I attempted to do an **rsync** backup following instructions on [THIS](http://www.mikerubel.org/computers/rsync_snapshots/) page, and right at the end of it, terminal spat this at me:

> 
sent 553819948 bytes  received 351086 bytes  2683636.97 bytes/sec
total size is 552690911  speedup is 1.00
rsync error: some files could not be transferred (code 23) at main.c(791)


Any idea what the error means?

---

### Post by EmmEff on 2006-02-16
What does your rsync command-line look like?

You might have tried to backup files that were deleted or volatile (ie. /proc filesystem).

---

