---
title: "truemobile 1150 - enable monitor mode"
date: 2009-01-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by arvindsaraf on 2009-01-01
I have an old Dell Inspiron 1100 with a PCMCIA TrueMobile 1150 wireless card running Ubuntu 7.10. The system works fine, with the drivers for the wireless card available with default installation.

However, I now want to use this card as an access point. I tried changing the wireless card into Master mode, but I am unable to do so:

$sudo iwconfig eth1 mode Master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device eth1 ; Operation not supported.

Ditto with modifying the /etc/network/interfaces file and then bringing up this interface.

I am not sure if the hardware doesn't support the Master mode, or if this is a firmware/driver issue. How do I find out? And if it is a driver issue, any suggestions for drivers compatible with this that support the mode?

Thanks,
Arvind

---

