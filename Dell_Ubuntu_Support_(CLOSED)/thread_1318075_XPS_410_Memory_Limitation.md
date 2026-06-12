---
title: "XPS 410 Memory Limitation?"
date: 2009-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by robertj20112 on 2009-11-07
I have recently upgraded my Dell XPS 410 to 64-bit Jaunty and would like to take advantage of it by expanding my computer's memory from 4GB to 8GB.  However, both the Dell site and the Crucial Technology site tell me my computer's max memory is 4GB.  The MB has 4 memory module slots and there are compatible 2GB memory modules, so 8GB would fit.  Is this a MB limitation? I have included below what I think is the pertinent configuration information.  Please let me know if more info is required.  Would appreciate any help, since I am clearly out of my depth here.  Thanks.

(P.S. Not sure why it shows memory as 5056 MB, as there are 4x1GB memory modules installed!)

description: Computer 
    width: 64 bits 
    capabilities: vsyscall64 vsyscall32 
  *-core 
       description: Motherboard 
       physical id: 0 
     *-memory 
          description: System memory 
          physical id: 0 
          size: 5056MiB 
     *-cpu 
          product: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz 
          vendor: Intel Corp. 
          physical id: 1 
          bus info: cpu@0 
          width: 64 bits 
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow vnmi flexpriority 
     *-pci 
          description: Host bridge 
          product: 82P965/G965 Memory Controller Hub 
          vendor: Intel Corporation 
          physical id: 100 
          bus info: pci@0000:00:00.0 
          version: 02 
          width: 32 bits 
          clock: 33MHz 
        *-pci:0 
             description: PCI bridge 
             product: 82P965/G965 PCI Express Root Port 
             vendor: Intel Corporation 
             physical id: 1 
             bus info: pci@0000:00:01.0 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci bus_master cap_list 
             configuration: driver=pcieport-driver 
           *-display 
                description: VGA compatible controller 
                product: GeForce 8600 GT 
                vendor: nVidia Corporation 
                physical id: 0 
                bus info: pci@0000:01:00.0 
                version: a1 
                width: 64 bits 
                clock: 33MHz 
                capabilities: bus_master cap_list 
                configuration: driver=nvidia latency=0 module=nvidia

---

### Post by TheHolm on 2009-11-08
You PC seems to be build on Intel® G965 chipset. It can address up to 8gig. Some part of address space is used for video card addressing. YOu never get 8 gig addressable memory.  So probaly Dell was right, you system can not support more than 4 gig memory.

---

### Post by robertj20112 on 2009-11-08
> **TheHolm said:**
> You PC seems to be build on Intel® G965 chipset. It can address up to 8gig. Some part of address space is used for video card addressing. YOu never get 8 gig addressable memory.  So probaly Dell was right, you system can not support more than 4 gig memory.

Thanks, TheHolm, for your quick reply.  I'm not sure I completely understand: if the G965 chipset can address up to 8GB, if the MB had 8GB installed, would I not get the benefit of any of that extra 4GB, or would the chipset not address any of the extra 4GB?  Also, any tips on what to look for in a future new computer to make sure it can handle 8GB of memory?

---

### Post by TheHolm on 2009-11-09
> **robertj20112 said:**
> Thanks, TheHolm, for your quick reply.  I'm not sure I completely understand: if the G965 chipset can address up to 8GB, if the MB had 8GB installed, would I not get the benefit of any of that extra 4GB, or would the chipset not address any of the extra 4GB?  


You actually get benefits from memory above 8 Gig.. As you stated in you fist mail you getting 5gig memory available. Remaining 3 gigs of memory are just not accessible. 

> **robertj20112 said:**
> Also, any tips on what to look for in a future new computer to make sure it can handle 8GB of memory?

Just read full system specification. Vendors rarely lie about such things as maximum supported memory.

---

### Post by MepisReign on 2009-12-03
8 GB of RAM is way too much, I have the same system and Ubuntu will use no more than 15% of the physical memory (4 GB), I don't see the need in upgrading to 8 GB.

Just my 2 cents

MepisReign ;)

---

