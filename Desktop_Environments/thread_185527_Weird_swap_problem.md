---
title: "Weird swap problem"
date: 2006-05-31
forum: Desktop Environments
---

### Post by pecanov on 2006-05-31
My computer has been running crazy when kswapd tries to free more memory (especially when there are two Eclipse instances running on XGL).

I've decided to do a check on the swap file, and it seems like it's not used.
When running *free*, I get:
> 
             total       used       free     shared    buffers     cached
Mem:          1010        976         33          0         29        438
-/+ buffers/cache:        509        501
Swap:            0          0          0

... and the situation is displayed the same in System Monitor.
But in fstab I have a line:
> /dev/hda6       none            swap    sw              0       0

So ... what is it? Is swap used or not? It surelly seems like it isn't. Anyone have a solution for this, or at least any expirience with this or something similar?

---

### Post by pecanov on 2006-05-31
I run the partition editor, and reformatted the partition.
It's fine now.

Sorry for posting here so soon before I run out of options.

It might however trick you in checking your swap ;)

---

