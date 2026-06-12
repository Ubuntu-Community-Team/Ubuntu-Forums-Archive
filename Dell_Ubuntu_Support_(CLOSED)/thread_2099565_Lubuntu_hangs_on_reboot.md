---
title: "Lubuntu hangs on reboot"
date: 2012-12-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Growlor on 2012-12-29
All,

I am running Lubuntu 12.04 (see below) on a Dell Lattitdue E5520 laptop. I set it up for dual boot with the Windows 7 pro it came with months ago when I first got it and everything works fine except: it will hang if I tell it to reboot (right about the time it would do a final system shutdown and start the actual power restart.)
If I tell it to shutdown, it works fine and if I tell it to shutdown or reboot when booted into Windows it works fine (so it's not a hardware issue), but the reboot hangs in Lubuntu. I did some checking and haven't been able to find anyone else reporting this issue, so figured I would mention it and give any required logs, etc to help debug it (if that will help - it's not really a show stopper for me as I just shutdown, then power-up when I need to reboot.)

Thanks,
Growlor


~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise

$ sudo lshw
[sudo] password for growlor: 
growlorPC      
    description: Laptop
    product: Latitude E5520 ()
    vendor: Winbond Electronics
    version: 01
    serial: [REDACTED - Growlor]
    width: 64 bits
    capabilities: smbios-2.6 dmi-2.6 vsyscall32
    configuration: boot=normal chassis=laptop uuid=44454C4C-5300-1044-8043-B1C04F365331
  *-core
       description: Motherboard
       product: 0KCT5J
       vendor: Winbond Electronics
       physical id: 0
       version: A01
       serial: [REDACTED - Growlor]
     *-firmware
          description: BIOS
          vendor: Winbond Electronics
          physical id: 0
          version: A05
          date: 11/30/2011
          size: 64KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2640M CPU @ 2.80GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2640M CPU @ 2.80GH
          serial: To Be Filled By O.E.M.
          slot: CPU 1
          size: 800MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz
          capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid cpufreq
          configuration: cores=2 enabledcores=2 threads=4
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal varies unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 4MiB
             capacity: 4MiB
             capabilities: internal varies unified
     *-memory
          description: System Memory
          physical id: 28
          slot: System board or motherboard
          size: 8GiB

---

