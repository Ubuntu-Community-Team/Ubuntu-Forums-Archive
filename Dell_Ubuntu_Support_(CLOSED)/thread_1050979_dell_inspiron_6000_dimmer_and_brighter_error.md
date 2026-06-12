---
title: "dell inspiron 6000 dimmer and brighter error"
date: 2009-01-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cagdas on 2009-01-26
when i dimming or brightening back light of the lcd panel ubuntu crashes or does not response! (ubuntu 8.10) is that error could be fixed?

ty all !!!

---

### Post by superm1 on 2009-01-26
> **cagdas said:**
> when i dimming or brightening back light of the lcd panel ubuntu crashes or does not response! (ubuntu 8.10) is that error could be fixed?

ty all !!!
There is a bug in the kernel.  You have to activate intrepid-proposed and pull in the updated kernel, headers and restricted modules packages.

See: [https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/261721) for more information.

---

