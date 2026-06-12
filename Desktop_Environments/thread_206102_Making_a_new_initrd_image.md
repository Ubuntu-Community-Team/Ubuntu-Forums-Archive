---
title: "Making a new initrd image"
date: 2006-06-29
forum: Desktop Environments
---

### Post by endfx on 2006-06-29
Can someone tell me howto make an initrd image from the /lib/modules/kernelversion?

In redhat they have a script called: mkinitrd that does this
but I how can I do this in ubuntu. 

I ask because the initrd for one of my kernels got deleted and now I can't boot that kernel.

Thanks.

---

### Post by tonyr on 2006-06-29
Can you just not find **mkinitrd**?  Install package **initrd-tools**.

If the kernel with the lost initrd.img is one of the standard ones, you could simply
re-install it.

In a terminal
```

sudo apt-get install --reinstall <kernel-package>

```

---

