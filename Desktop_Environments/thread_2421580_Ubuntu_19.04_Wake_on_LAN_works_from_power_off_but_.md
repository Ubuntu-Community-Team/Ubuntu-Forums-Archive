---
title: "Ubuntu 19.04 Wake on LAN works from power off but not from suspend."
date: 2019-06-24
forum: Desktop Environments
---

### Post by peter-a on 2019-06-24
Ubuntu 19.04

Wake on LAN used to work perfectly. Now, if I shut down, I can start up using a WoL magic packet. However, if I suspend using the alt-click on the power icon, it successfully suspends but refuses to WoL.

ethtool sets WoL to g and I even have a script which sets this option on every boot, just in case.

Clearly, this is not a problem with hardware or BIOS because a) it used to work before 19.04 and b) it works when Ubuntu is shut down.

I've seen references to setting netdown=no in various system halt files, but I've seen different file locations for different Ubuntu versions, none of them 19.04/.

Any ideas?

---

### Post by rondiamond on 2020-01-16
I am in a similar situation, cannot be a bios or hardware issue as this was working perfectly with Windows.

With Ubuntu 16.04 & 18.04 behaviour is always the same.. works perfectly from shutdown but when attempting to wol from Hibernate or Suspend, LAN port is always active but the system does not wake.

I am convinced the problem must be either driver or acpi related.

Has anybody figured out a solution to this?

---

