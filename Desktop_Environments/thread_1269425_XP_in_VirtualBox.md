---
title: "XP in VirtualBox"
date: 2009-09-18
forum: Desktop Environments
---

### Post by Pengwyn44 on 2009-09-18
I have created an XP virtual machine using VirtualBox downloaded with Synaptic. I have allocated 10GB for the hard drive and 1GB for memory, the cpu speed is 3MHz. Main OS is 9.04. All is well except that there is a problem with playing sounds.
XP recognises a data CD but not an audio CD, neither does it play default Windows sounds at start up and close down. XP control panel reports that all is well with the sound card etc. I have loaded the Windows motherboard drivers into the running XP therefore all (in theory) should work.

Has anyone any idea of what may be wrong please?

PROBLEM SOLVED

---

### Post by Drone022 on 2009-09-18
Did you try all the soundcard emulation choices? Only one of them works properly for me, I think my current version of virtualbox has about 4 to choose from.

---

### Post by Pengwyn44 on 2009-09-18
Thanks for the suggestion. I have now found the problem's answer in the VirtulBox helpfile on the LinuxFormat DVD.

The VBox audio driver has to be set at PULSE AUDIO for Linux hosts.

---

