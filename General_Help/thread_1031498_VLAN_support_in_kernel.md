---
title: "VLAN support in kernel"
date: 2009-01-05
forum: General Help
---

### Post by xyz_123 on 2009-01-05
I have implemented a layer 2 **raw socket program**. The maximum size of the packet is 1514 bytes, where 14 bytes are reserved for the Ethernet header. However, I want the layer 2 to send VLAN packets, that is, the header should be of 18 bytes length.
Presently I am working on Ubuntu 8.04 Kernel version 2.6.24. What do I need to do to be able to send VLAN packets in the raw socket program, that is, Ethernet packets with 18 bytes of header containing 4 bytes of VLAN information?

---

