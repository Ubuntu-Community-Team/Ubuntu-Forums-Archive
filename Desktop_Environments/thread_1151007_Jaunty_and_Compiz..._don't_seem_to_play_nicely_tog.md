---
title: "Jaunty and Compiz... don't seem to play nicely together"
date: 2009-05-06
forum: Desktop Environments
---

### Post by bcrudo on 2009-05-06
Hey all,

I'm not sure if it's just me or what but for some reason Compiz no longer works. I upgraded to Jaunty from Intrepid and as far as I can tell thus far everything seems to be going well except for the fact that Compiz doesn't work. If anyone has some advice about how to get back on track I'd be grateful.

Thanks again

laptop specifications
_______________________________________
    description: Notebook
    product: Satellite A200
    vendor: TOSHIBA
    version: PSAE3*-TH108C
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
  *-core
       description: Motherboard
       product: ISKAA
       vendor: TOSHIBA
       physical id: 0
       version: 1.00
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.60 (08/28/2008)
          size: 106KiB
          capabilities: isa pci pcmcia pnp upgrade shadowing escd cdboot acpi usb agp biosbootspecification
     *-cpu:0
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5450  @ 1.66GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.15.13
          slot: U2E1
          size: 1GHz
          capacity: 4096MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
          configuration: id=0
     *-memory
          description: System Memory
          physical id: d
          slot: System board or motherboard
          size: 2GiB
        *-bank:0
             description: SODIMM Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: M1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)

---

### Post by bcrudo on 2009-05-06
Ok... I have solved my issue and thought I would share my findings

The problem was that Compiz was NOT loading at startup so In order to fix the problem. 

I used the Startup Applications program located here:  System --> Preferences --> Startup Applications
                        Than I added a new entry by pushing:   Add+
                                               In the Name field I used:   Compiz
                                        In the Command field I used:   fusion-icon
                                                       and finally clicked:   OK
 
That did the trick... 
                               hope this helps

---

