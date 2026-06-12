---
title: "Why network manager does not have virtual IP option?"
date: 2009-02-27
forum: General Help
---

### Post by cd-r80 on 2009-02-27
Why network manager does not have virtual IP option? Always I have to remove NM & configure manual.

---

### Post by blackgr on 2009-02-27
Virtual IPs is server oriented where there is no X. NM is desktop-noob oriented

---

### Post by DGortze380 on 2009-02-27
> **cd-r80 said:**
> Why network manager does not have virtual IP option? Always I have to remove NM & configure manual.

You shouldn't have to remove it.

sudo ifconfig [int]:[#] [address] netmask [netmask]

/etc/network/interfaces for persistent configurations.

And yes, typically a configuration used on servers, the vase majority of desktop users don't even know what a Virtual NIC is.

---

