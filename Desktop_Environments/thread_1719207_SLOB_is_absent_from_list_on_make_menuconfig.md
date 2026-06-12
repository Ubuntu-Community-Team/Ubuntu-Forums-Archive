---
title: "SLOB is absent from list on make menuconfig"
date: 2011-04-01
forum: Desktop Environments
---

### Post by rchan0021 on 2011-04-01
Hello all,

    I am trying to make the kernel use the SLOB allocator instead of SLAB. But when I am in the configuration menu SLOB does not appear as an option.


Help please.

---

### Post by taxicat on 2012-12-01
In ```
make menuconfig
``` you select ```
General setup->Configure standard kernel features (expert users)
``` and the SLOB allocator will then be present in  ```
General setup->Choose SLAB allocator
```

As to anyone who will whine about digging up an old thread. This is the top and only result on google for this issue. Just trying to post a solution where one isn't. Cheers.

---

