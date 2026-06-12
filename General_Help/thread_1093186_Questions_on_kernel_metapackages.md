---
title: "Questions on kernel metapackages"
date: 2009-03-11
forum: General Help
---

### Post by syvehc on 2009-03-11
I have some questions on kernel metapackages.  Here is what I found for an explanation of these packages (below in question 1.).  Now I think I understand why they have these, so that it will be easier for people to upgrade and try different kernels.

I have three questions about this stuff.

1. These descriptions below don't really make sense to me.  What is each one for and what are the advantages?

Kernel Metapackages

      linux-generic: Always depends on the latest generic Linux kernel available.
    *

      linux-headers-generic: This package always depends on the latest generic kernel headers available.
    *

      linux-image-generic: This package always depends on the latest generic kernel image available.
    *

      linux-restricted-modules-generic: This package always depends on the latest restricted modules available for generic kernels.


2. Does update manager install kernel packages and why (I would assume because of security and bugs)?  

3. If I try one of these kernels using the synaptic manager will it add a boot loader for my old kernel in grub.

Thanks in advance

---

