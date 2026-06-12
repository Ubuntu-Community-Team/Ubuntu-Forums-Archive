---
title: "Custom Kernel Help?"
date: 2009-05-14
forum: General Help
---

### Post by ebanlague on 2009-05-14
I've seen multiple Kernels tossed around for your computer specs, but all the threads and such are from [seemingly] past years, with the highest end kernel I've seen having support for booting with only a dual core.

Is there a custom Kernel or something of the like for us Quad-core users? Maybe shave some boot time off? My current Kernel is the one packaged with 9.04 AMD64.

---

### Post by mbsullivan on 2009-05-14
> Is there a custom Kernel or something of the like for us Quad-core users? Maybe shave some boot time off? My current Kernel is the one packaged with 9.04 AMD64.

There are kernel options for tailoring an install towards a specific architecture. Using the "Core2/New Xeon" (or something like that) option instead of generic i686 might make the kernel nominally faster.

However, it won't really speed up boot time, and probably isn't worth the effort. The packaged kernels already support SMPs fairly well.

Just my thoughts... I could be wrong.
Mike

---

