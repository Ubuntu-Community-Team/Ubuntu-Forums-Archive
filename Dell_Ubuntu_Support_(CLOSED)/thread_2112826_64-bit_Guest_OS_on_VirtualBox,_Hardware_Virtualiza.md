---
title: "64-bit Guest OS on VirtualBox, Hardware Virtualization, Ubuntu - Dell 1545"
date: 2013-02-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by RSASKA on 2013-02-05
Hello,

I installed Ubuntu 11.04 on Dell 1545 laptop.

I have also installed VirtualBox and it has worked well. But when I attempt to install 64-bit OS, i.e. Win Server 2008, I am told that my processor must be enabled for hardware virtualization.

But how do I know if my processor is enabled? The processor I have is 

Processor 0: Intel(R) Core(TM) 2 DUO CPU
Processor 1: Intel(R) Core(TM) 2 DUO CPU

I googled this and was told to download Intel Processor Identification Utility ([http://www.intel.com/p/en_US/support/highlights/processors/toolspiu](http://www.intel.com/p/en_US/support/highlights/processors/toolspiu)). Because it does not run on Ubuntu, I ran this on one of my virtual OS, which is Windows 2003, 32-bit, and I get error everytime I try to run the program.

Please help me. I need to install WIndows Server 2008 on VirtualBox. I need to know if the processor is capable of hardware virtualization, and if so, how to make it work so that I can successfully install 2003 as guest OS.


Thank you!!!

---

### Post by RaHorakhty on 2013-03-14
hm seems like its an issue with a BIOS setting.  I would check with the Vbox msg board....

---

### Post by itrogers on 2013-03-14
Look for a setting in the BIOS to enable hardware / CPU virtualization.

---

### Post by ibjsb4 on 2013-03-14
Which core2 are you running?  Check here for VT.

[http://ark.intel.com/products/family/26547/Intel-Core2-Duo-Desktop-Processor/desktop](http://ark.intel.com/products/family/26547/Intel-Core2-Duo-Desktop-Processor/desktop)

---

