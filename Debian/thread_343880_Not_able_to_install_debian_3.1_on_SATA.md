---
title: "Not able to install debian 3.1 on SATA"
date: 2007-01-22
forum: Debian
---

### Post by saikumar_divvela on 2007-01-22
Hi, 

I am trying to install Debian 3.1 sarge using CD on IBM server X3550 type 7978 model 42A, which has two SATA hard disks and INTEL chipset. The server supports raid functionality.
I gave boot option linux26.  Debain is not able to  detect hard disk and failing.
I tried installation using boot parameters pci=nomsi and acpi=force irqpoll and still hard disk is not  detected. Have any one faced this kind of problem. Does debian 3.1 support SATA hard disks. 
Any information on this would be appreciated much.


Thanks,
Sai

---

### Post by patrickfromspain on 2007-01-22
I'd try Debian Etch and forget about Sarge.. Sarge is pretty old (more than a year.. this is a lot in the linux scene).

---

### Post by fluffnik on 2007-01-24
> **saikumar_divvela said:**
> Hi, 

I am trying to install Debian 3.1 sarge using CD on IBM server X3550 type 7978 model 42A, which has two SATA hard disks and INTEL chipset. The server supports raid functionality.
I gave boot option linux26.  Debain is not able to  detect hard disk and failing.
I tried installation using boot parameters pci=nomsi and acpi=force irqpoll and still hard disk is not  detected. Have any one faced this kind of problem. Does debian 3.1 support SATA hard disks. 
Any information on this would be appreciated much.

I had a problem with an X206 8482-9NG with the ICH6 chipset; it lost the PATA CDROM due to lack of ATAPI support in the installer's kernel module...

Not the same problem but probably down to the same module.

My solution was to use the latest Debian Installer business card snapshot from [here.]("http://www.debian.org/devel/debian-installer/")

---

### Post by kinematic on 2007-01-24
debian sarge is ancient....i go with etch if i were you.
etch has been frozen and the only thing left to do is get the bugs down to a release level.
i've been running testing for months now and it's incredibly stable.

---

