---
title: "Intel PWLA8391GTBLK NIC Inspiron 530"
date: 2008-04-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by WCD on 2008-04-23
Has anyone successfully gotten a gigabit lan card to work on an Inspiron 530 running 64-bit Hardy?  I'm trying to install an Intel PWLA8391GT and get ata errors everytime I plug it in.  Remove it and all is well.  I've tried disabling the onboard nic and using the noacpi and acpi=off options to no avail.  I do not see an IRQ conflict.  Where do I start with this?

---

### Post by aaazman on 2008-04-28
I ran Ubuntu 8.04 LiveCD with a D-Link DGE-530T Gigabit Ethernet Adapter (rev.B) NIC well. However, the problem, I found with the help from some other posts is, you have to go to the the BIOS Setup (i.e., F2 at reboot) and change your SATA mode from IDE to RAID. That was the major culprit.

---

