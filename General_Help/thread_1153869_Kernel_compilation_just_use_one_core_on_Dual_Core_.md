---
title: "Kernel compilation: just use one core on Dual Core machine"
date: 2009-05-09
forum: General Help
---

### Post by grubby23 on 2009-05-09
Hi

This might sound now like a bit a dull question, but I wonder if it is possible to use some
parameter configuration during kernel compilation so that Linux just uses one of the two
CPUs on a Dual Core machine. I have to do some performance measurements, and a second core
would make the results less accurate in my case. 

At the moment I use for compilation the following command : 

CONCURRENCY_LEVEL=3 make-kpkg --initrd --revision=386 kernel_image 
kernel_headers modules_image

Or maybe there is another simple way to deactivate the second core? 

Many thanks

---

