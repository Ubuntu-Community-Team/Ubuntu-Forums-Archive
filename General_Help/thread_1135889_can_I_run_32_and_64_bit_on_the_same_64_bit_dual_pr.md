---
title: "can I run 32 and 64 bit on the same 64 bit dual processor?"
date: 2009-04-24
forum: General Help
---

### Post by rsnow on 2009-04-24
I am currently running XP 32 bit on amd64 bit 2 core Motherboard. Would there be problems with installing 9.04 64 bit either as a dual boot or into Virtualbox?

---

### Post by WRDN on 2009-04-24
You can't install 64bit OS' in VirtualBox currently (as far as I know), as it emulates a 32bit CPU. There should be no reason why you couldn't dual boot, though, this is not to say you may not have any problems (other hardware may not be compatible).

---

### Post by zvacet on 2009-04-24
You can install 64 bit Ubuntu in Virtualbox PUEL version (maybe it is possible in OSE ).If reason for running 64-bit is not ram I don´t see reason not to continue with 32-bit.In any case [here]("http://ubuntuforums.org/showthread.php?t=1074160") is good tutorial for installing Virtual box.Other solution is dual boot.

---

### Post by jespdj on 2009-04-24
> **WRDN said:**
> You can't install 64bit OS' in VirtualBox currently (as far as I know), as it emulates a 32bit CPU.
Yes you can, that capability has been added to VirtualBox a few versions back (at least half a year ago).

---

### Post by Monotoko on 2009-04-24
but if you were running a 32bit version of Windows as your host...i dont think you could make it run 64bit guest could you?? :S

---

### Post by kpatz on 2009-04-24
A 32-bit host can only run 32-bit guests.  This includes 32-bit host OSes running on 64-bit CPUs.

A 64-bit host can run 32-bit and 64-bit guests.

---

### Post by dcstar on 2009-04-24
> **kpatz said:**
> A 32-bit host can only run 32-bit guests.  This includes 32-bit host OSes running on 64-bit CPUs.

A 64-bit host can run 32-bit and 64-bit guests.

Yep, I run 32-bit XP and 32 & 64-bit Ubuntu versions under my 64-bit Ubuntu host (in VMWare Server 1.09).

---

### Post by evermooingcow on 2009-04-24
AFAIK you can only run 64bit guests on VirtualBox if your CPU supports VT (AMD-v, VT-x). Remember to enable it in the BIOS too. I don't know if your host has to be 64bit.  VMware is capable of running 64bit guests on 64 or 32bit hosts and in either case without the need for VT.

---

### Post by rsnow on 2009-04-25
Thanks to all. I haven't decided yet which setup I will go with but your input has been a great help.

---

