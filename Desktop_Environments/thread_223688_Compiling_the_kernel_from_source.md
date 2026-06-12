---
title: "Compiling the kernel from source"
date: 2006-07-26
forum: Desktop Environments
---

### Post by zarathustra on 2006-07-26
Just a quick question: do you still need to install the EVMS patch from the repositories on the new kernels?

---

### Post by mlind on 2006-07-26
> **zarathustra said:**
> Just a quick question: do you still need to install the EVMS patch from the repositories on the new kernels?

Do you mean upsteam kernel or Ubuntu kernel?
For upsteam kernels, you always need to perform one the [3 fixes]("http://evms.sourceforge.net/install/kernel.html#bdclaim") if you plan to use emvs.

---

### Post by zarathustra on 2006-07-26
OK thanks, I was referring to vanilla kernels downloading from the kernel.org archives.

---

### Post by mlind on 2006-07-26
> **zarathustra said:**
> OK thanks, I was referring to vanilla kernels downloading from the kernel.org archives.

I'm actually looking the same issue myself. I wonder what would be the best solution: patch the kernel, disable evms using update-rc or excluding my partitions to /etc/evms.conf. 
I'm not going to use evms anyway, although it seems to offer nice set of features.

Now half of my partitions are being managed by evms, except root partition.

---

