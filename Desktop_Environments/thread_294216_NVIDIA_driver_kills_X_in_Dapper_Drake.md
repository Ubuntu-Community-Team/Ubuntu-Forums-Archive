---
title: "NVIDIA driver kills X in Dapper Drake"
date: 2006-11-06
forum: Desktop Environments
---

### Post by khafra on 2006-11-06
I have a "GIGABYTE GV-NX78T256VB-ED GeForce 7800GT 256MB GDDR3 PCI Express x16 Video Card" which worked fine under dapper drake.  But with edgy eft, when I install the driver with synaptic and then run the included setup program, it tells me my x configuration has changed, it's unable to continue, and to reset the hash or manually add "nvidia" in place of "nv" in the x config file.

When I do any of the last two options, X won't start.  Waaaaah! I want my hardware acceleration!

---

### Post by Paul41 on 2006-11-06
Do you have the linux-restriced-modules installed for the kernel you are using?

---

### Post by khafra on 2006-11-06
I do have 'em installed.

---

### Post by khafra on 2006-11-07
Checked again--I've still got linux-restricted-modules-386 installed.  Any other reason it'd fail?

---

