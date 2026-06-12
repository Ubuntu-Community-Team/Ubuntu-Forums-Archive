---
title: "How to uninstall older kernel versions?"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Roobert on 2006-07-18
I have way too many entries on my boot screen; I think about 5 or 6 kernel versions going all the way back to the Breezy Badger days. How do I uninstall the old ones?

---

### Post by christhemonkey on 2006-07-18
Go into synaptic, and search for linux-image.
There should be 5 or 6, I try and make sure to keep my current one, and one other that is firm and stable.
Just in case!

---

### Post by geco on 2006-07-18
> **Roobert said:**
> I have way too many entries on my boot screen; I think about 5 or 6 kernel versions going all the way back to the Breezy Badger days. How do I uninstall the old ones?

from terminal
```

apt-get remove linux-image-KERNEL_VERSION

```

you can check the kernel version by typing TAB

;)

---

### Post by Roobert on 2006-07-19
Great, thanks that worked!

:D

---

