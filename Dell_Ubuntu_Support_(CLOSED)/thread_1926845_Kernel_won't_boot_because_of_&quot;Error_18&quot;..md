---
title: "Kernel won't boot because of &quot;Error 18&quot;."
date: 2012-02-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by peterdm on 2012-02-17
System:
* Dell Precision T3500
* Ubuntu 11.10, kernel 3.0.0-14-generic-pae
* BIOS version A09

Kernels 3.0.0-15 and 3.0.0-16 won't boot because of "Error 18: Selected cylinder exceeds maximum supported by BIOS". Everything worked fine up until kernel 3.0.0-14 (I am currently still using 3.0.0-14 as workaround).

I've looked on the internet for some answers, this is what I checked so far:
* Some suggested it was due to an old GRUB. I have been on GRUB2 for some time now, so that's not it.
* Some suggested it is because the system is too old. But that doesn't explain why everything works fine with an older kernel.
* Some suggested it is a hardware failure. Again, that doesn't explain why everything works fine with an older kernel.

Any other ideas?

---

### Post by peterdm on 2012-04-05
This has been fixed in recent kernels (intentionally or not).

---

