---
title: "Gutsy: Dell 820N Core 2 Duo not detected as SMP"
date: 2007-12-11
forum: Dell  Ubuntu Support
---

### Post by abierbaum on 2007-12-11
I have a Dell Latitude D820N Duo system with an Intel Core 2 Duo T7200 CPU.  When ran fiesty, the system was correctly identified as having two CPUs and everything worked fine.  Now that I am running gutsy, the kernel is not allowing both CPUs to be enabled.  I have attached the dmesg output, but I think this is the relevant part below.  

Any ideas?

Thanks,
Allen


------------------------------------------------------------------------
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515523
[    0.000000] Kernel command line: root=UUID=c0c2e12d-09d7-491f-b362-0afcb527e51d ro noapic quiet
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   18.158658] time.c: Detected 1995.003 MHz processor.
[   18.180764] Console: colour VGA+ 80x25
[   18.180783] Checking aperture...
[   18.180795] Calgary: detecting Calgary via BIOS EBDA area
[   18.180797] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   18.351485] Memory: 2054628k/2095620k available (2274k kernel code, 40604k reserved, 1181k data, 296k init)
[   18.351536] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   18.588298] Calibrating delay using timer specific routine.. 11974.00 BogoMIPS (lpj=23948005)
[   18.588499] Security Framework v1.0.0 initialized
[   18.588508] SELinux:  Disabled at boot.
[   18.588714] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   18.590373] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   18.591157] Mount-cache hash table entries: 256
[   18.591317] CPU: L1 I cache: 32K, L1 D cache: 32K
[   18.591321] CPU: L2 cache: 4096K
[   18.591324] CPU 0/0 -> Node 0
[   18.591326] using mwait in idle threads.
[   18.591328] CPU: Physical Processor ID: 0
[   18.591329] CPU: Processor Core ID: 0
[   18.591336] CPU0: Thermal monitoring enabled (TM2)
[   18.591349] SMP alternatives: switching to UP code
[   18.591657] Early unpacking initramfs... done
[   20.797826] ACPI: Core revision 20070126
[   20.797868] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.819945] ACPI: setting ELCR to 0200 (from 0e28)
[   20.821068] SMP motherboard not detected.
[   20.821072] Using local APIC timer interrupts.
[   20.871172] result 10390626
[   20.871174] Detected 10.390 MHz APIC timer.
[   20.875048] SMP disabled
[   20.875077] Brought up 1 CPUs
[   20.875226] NET: Registered protocol family 16
--------------------------------------------------------------------------------------

---

