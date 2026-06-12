---
title: "kvm -  kernel virtual machine support."
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by rozen on 2007-07-26
I recently purchased an XPS 410 with Linux installed and I would like to use kvm virtualization but it appears that the hardware, specifically the BIOS does not support the function.  Has anyone been able to either get a supporting BIOS or run kvm somehow?

I will certainly appreciate any pointers.

Thanks in Advance,
Don

---

### Post by ansicplusplus on 2007-07-29
Dear Don,

if your hardware doesn't support virtualization, then you can't use kvm. A BIOS update won't change this. kvm depends on the virtualization features provided by your cpu.

kvm is still experimental -- although it grows quite fast. The version included in Feisty already works quite well, therefore I am looking forward to ubuntu's next version when kvm hopefully will be updated.

I suggest you use one of the other VM products as f.e. VMWare, VirtualBox or Qemu. They don't depend on your cpu and are more reliable -- currently.

Yours,
ansicplusplus

---

### Post by deserthowler on 2007-07-29
I found Virtual Box to work well on my GX 110 with 512 GB memory and a PIII 866 processor.  I run it under both Debian Etch and Ubuntu 6.06.  I don't know about anything else.

Earl

---

### Post by sciurus on 2007-07-29
> **ansicplusplus said:**
> Dear Don,

if your hardware doesn't support virtualization, then you can't use kvm. A BIOS update won't change this. kvm depends on the virtualization features provided by your cpu.



Based on what I've read, this isn't true. It is possible for a CPU to support VT, but not the BIOS. A BIOS update could then enable KVM. There may also be a BIOS option to enable or disable VT.

"Intel® Virtualization Technology (Intel® VT), Intel® Trusted Execution Technology (Intel® TXT), and Intel® 64 architecture require a computer system with a processor, chipset, BIOS, enabling software and/or operating system, device drivers and applications designed for these features."

[http://www.intel.com/design/pentium4/datashts/306382.htm](http://www.intel.com/design/pentium4/datashts/306382.htm)

---

### Post by ansicplusplus on 2007-11-04
> **sciurus said:**
> Based on what I've read, this isn't true. It is possible for a CPU to support VT, but not the BIOS. A BIOS update could then enable KVM. 
...


Dear sciurus, 

what you point out is exactly the same i wrote. Of course it is possible for a cpu (i.e. hardware) to support VT and to have a BIOS that doesn't. In this case a BIOS update usually works. But if a cpu doesn't support VT then a BIOS supporting it won't enable you to use VT. Otherwise it wouldn't be a cpu feature, would it ?

Yours,
ansicplusplus

---

