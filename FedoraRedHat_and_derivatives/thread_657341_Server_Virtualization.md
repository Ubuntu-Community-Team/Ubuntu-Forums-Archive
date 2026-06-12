---
title: "Server Virtualization"
date: 2008-01-03
forum: Fedora/RedHat and derivatives
---

### Post by john_sm on 2008-01-03
Hey Folks - We need your help. We were hoping, we could gain from your experience with implementing server virtualization. When should we be using Red Hat Virtualization, Citrix Virtualization, Xen Virtualization, Microsoft Virtualization, Oracle Virtualization and VMWare.  I will be very interested in learning from your first hand experince.  I will also like to know, under what situations is one virtualization prefered over the other.  - Thanks for your help

---

### Post by jinx099 on 2008-01-04
I know the most about VMWare and Xen, so I will comment on those.  VMWare is full virtualization as opposed to Xen with is paravirtualized.  Full virtualization will basically emulate an entire PC and all hardware.  This means you can install whatever you want at the cost of performance.

Xen on the otherhand is less "virtualized" wich means you can only run xen-enabled OSes, but the performance is much better than VMWare.

I hope this helps you a bit!

---

