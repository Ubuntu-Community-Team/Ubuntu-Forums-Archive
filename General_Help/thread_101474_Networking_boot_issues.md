---
title: "Networking boot issues"
date: 2005-12-09
forum: General Help
---

### Post by mrpaco on 2005-12-09
Hi all,

Recently, I configured my laptop's Broadcom BCMWL5 integrated wireless card on Breezy Badger using ndiswrapper 1.1, which was obtained through Synaptic Package Manager.  When everything was sucessfully set up, I added the ndiswrapper module to etc/modules, and proceeded to reboot.  When Ubuntu began to boot again, it hung for approx. 1-2 minutes at "Configuring network interfaces" and for another minute or so at "Waiting for network interface to come up".  Even before this, I noticed that it will also hang at "Waiting for network interface to come up" when there is no ethernet cable plugged into my NIC.  Outside of this, everything works fine.  The kernel that I am running is 2.6.12-10-k7.  Are there any workarounds for these issues?  Obviously, removing ndiswrapper from etc/modules would address the first issue, but would also be a major inconvenience.  Any help would be greatly appreciated.

---

### Post by emerick7 on 2005-12-09
i'm having the same problem with my internet and ndiswrapper (I also get the hanging on configuring network interfaces)... i've tried a bunch of things but nothing has worked

---

