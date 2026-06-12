---
title: "Kernel Panic - VFS: Unable to mount root fs on unknown-block (0,0)"
date: 2009-01-15
forum: General Help
---

### Post by kesre on 2009-01-15
Hi


I recently got Ubuntu (Ibex) and I started noticing that if I left the computer on for long periods of time (overnight) in the morning, the screen would freeze with just the Desktop image displaying.

now, I know that when the system freezes you want it to shutdown 'gracefully' unfortunately, Ubuntu does not recognize my keyboard's SySrq key. The key is [FN] + delete. However, it is recognized as "prt sc" (as is the actual prt sc)
I have a compaq presario V6000, 88 keys, 101 compatible... and so on.


Usually when I hard reset, the computer is fine, however, now I get
Code:

1.484036 RAMDisk: Compressed image found at block 0
1.890479 - list of all partitions:
1.890536 No filesystem could mount root, tried: cramfs
1.891310 Kernel Panic - not syncing:VFS: Unable to mount root fs on unknown-block (0,0)

I assume this is due to not being able to use
Alt + Sysrq R,E,I,S,U,B
 - so the disk doesn't sync...

If you can help me on any one of these parts, I would greatly appreciate it (though I think I'll need to be able to startup Ubuntu to troubleshoot the 2nd and 1st Parts...

Thanks in advance

---

### Post by RJARRRPCGP on 2009-01-16
Sounds like a hardware problem. Sorry. Not normal to freeze like that.

---

### Post by kesre on 2009-01-16
Hmmm... Ok

Is there a way to identify the hardware problem? 

XP runs fine, and I'm using the Ibex live CD right now...

---

### Post by RJARRRPCGP on 2009-01-16
> **kesre said:**
> Hmmm... Ok

Is there a way to identify the hardware problem? 

XP runs fine, and I'm using the Ibex live CD right now...

It sounds like you have sectors getting ready to go bad on the HDD or your temps. are too high.

---

### Post by kesre on 2009-01-17
@ sectors issue:
Is there a method to verify this? and how do I fix it?

as for temp, that sounds very plausible -cpu temp is usually between 40-60 deg C, but the hard disk gets really hot sometimes - Is there a way to fix this (and why doesn't it boot up even after being left off for a long period of time?)

What should I do to prevent these things in the future?

---

### Post by Nicram on 2009-01-17
The same here. But it could be something else that hardware problem.
Try booting into older kernel, it works for me.

---

### Post by kesre on 2009-01-17
Ok. Thanks for the tip!

How would I boot into an older kernel from the startup?

---

### Post by Nicram on 2009-01-17
> **kesre said:**
> 
How would I boot into an older kernel from the startup?
Just after bios boot, select kernel name with lower number in grub menu

---

### Post by kesre on 2009-01-17
Excellent! It's working now.

---

### Post by Nicram on 2009-01-17
> **kesre said:**
> Excellent! It's working now.
Glad to hear that, still it's rather a workaround than a solution.
I'm wondering what the real problem is?

---

### Post by kesre on 2009-01-17
Right.

Now that I'm actually in Ubuntu, are there any commands I can run to give us useful logs?

---

### Post by Nicram on 2009-01-17
> **kesre said:**
> 
  are there any commands I can run to give us useful logs?
Sorry, I don't know and I'm too busy to search right now.
Still, if you find something please share with our community.
This is what Ubuntu means, right?

---

### Post by kesre on 2009-01-18
Ok, heres something new:

when I boot from the latest kernel, after the normal scrolling of stuff starting up the screen shows the previous error data, then clears the screen and prints 

(paraphrased) - Boot from ext3, starting up...

then

```
0.319595 ACPI: Aborted because bad gzip magic numbers
1.874563 Kernel Panic - not syncing...
```

Then the whole "VFS: Unable to mount" thing

Does that help at all?

(didn't know that Ubuntu used magic)

---

### Post by kesre on 2009-01-19
Ok, after lookin through some sites - they said var/log/messages might be helpful

This is a log of a reboot when I loaded the latest kernel (and it crashed)

I included a little before and after


```
Jan 13 12:08:00 Kesre-laptop -- MARK --
Jan 13 12:18:28 Kesre-laptop pulseaudio[5948]: protocol-native.c: Failed to push data into queue
Jan 13 12:18:29 Kesre-laptop last message repeated 8460 times
Jan 13 12:48:00 Kesre-laptop -- MARK --
Jan 13 13:08:00 Kesre-laptop -- MARK --
Jan 13 13:28:00 Kesre-laptop -- MARK --
Jan 13 13:48:00 Kesre-laptop -- MARK --
Jan 13 14:08:00 Kesre-laptop -- MARK --
Jan 13 14:28:00 Kesre-laptop -- MARK --
Jan 13 14:48:00 Kesre-laptop -- MARK --
Jan 13 15:08:00 Kesre-laptop -- MARK --
Jan 13 15:28:00 Kesre-laptop -- MARK --
Jan 13 15:48:00 Kesre-laptop -- MARK --
Jan 13 16:08:00 Kesre-laptop -- MARK --
Jan 13 16:25:23 Kesre-laptop syslogd 1.5.0#2ubuntu6: restart.
Jan 13 16:25:23 Kesre-laptop kernel: Inspecting /boot/System.map-2.6.27-9-generic
Jan 13 16:25:23 Kesre-laptop kernel: Cannot find map file.
Jan 13 16:25:23 Kesre-laptop kernel: Loaded 51782 symbols from 96 modules.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Initializing cgroup subsys cpu
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-9.19-generic)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] BIOS-provided physical RAM map:
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f6d0000 (usable)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 000000007f6d0000 - 000000007f6e3000 (ACPI NVS)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 000000007f6e3000 - 0000000080000000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] last_pfn = 0x7f6d0 max_arch_pfn = 0x100000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] RAMDISK: 3781f000 - 37fef654
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] DMI present.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: RSDP 000F8480, 0024 (r2 HP    )
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: XSDT 7F6D5ABA, 0084 (r1 HPQOEM SLIC-MPC  6040000  LTP        0)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: FACP 7F6DFC6C, 00F4 (r3 HP     30CC      6040000 ALAN        1)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: DSDT 7F6D705F, 8B99 (r1 HP     30CC      6040000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: FACS 7F6E2FC0, 0040
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: HPET 7F6DFD60, 0038 (r1 HP     30CC      6040000 LOHR       5A)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: MCFG 7F6DFD98, 003C (r1 HP     30CC      6040000 LOHR       5A)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: TMOR 7F6DFDD4, 0026 (r1 HP     30CC      6040000 PTL         3)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: APIC 7F6DFDFA, 0068 (r1 HP     30CC      6040000  LTP        0)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: BOOT 7F6DFE62, 0028 (r1 HP     30CC      6040000  LTP        1)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: SLIC 7F6DFE8A, 0176 (r1 HPQOEM SLIC-MPC  6040000  LTP        1)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: SSDT 7F6D6D82, 02DD (r1 HP     30CC         1000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: SSDT 7F6D6CDA, 00A8 (r1 HP     30CC         1000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: SSDT 7F6D60CA, 025F (r1  HP    30CC         3000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: SSDT 7F6D6024, 00A6 (r1  HP    30CC         3000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: SSDT 7F6D5B3E, 04E6 (r1  HP     30CC        3000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: DMI detected: Hewlett-Packard
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] 1142MB HIGHMEM available.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] 896MB LOWMEM available.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   mapped low ram: 0 - 38000000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   low ram: 00000000 - 38000000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   bootmap 00008000 - 0000f000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #4 [003781f000 - 0037fef654]          RAMDISK ==> [003781f000 - 0037fef654]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #6 [000009f800 - 0000100000]    BIOS reserved ==> [000009f800 - 0000100000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #7 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] found SMP MP-table at [c00f8520] 000f8520
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Zone PFN ranges:
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]   HighMem  0x00038000 -> 0x0007f6d0
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Movable zone start PFN for each node
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000]     0: 0x00000100 -> 0x0007f6d0
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000dc000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] PM: Registered nosave memory: 00000000000dc000 - 0000000000100000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 517251
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Kernel command line: root=UUID=3b1e5037-25e6-473d-b681-3f50fa90da0c ro quiet splash 
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Initializing CPU#0
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Extended CMOS year: 2000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] TSC: using PMTIMER calibration value
Jan 13 16:25:23 Kesre-laptop kernel: [    0.000000] Detected 1995.199 MHz processor.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Console: colour VGA+ 80x25
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] console [tty0] enabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Memory: 2054248k/2087744k available (2572k kernel code, 32192k reserved, 1160k data, 424k init, 1170240k highmem)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] virtual kernel memory layout:
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000]       .init : 0xc04ab000 - 0xc0515000   ( 424 kB)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000]       .data : 0xc038335a - 0xc04a5680   (1160 kB)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000]       .text : 0xc0100000 - 0xc038335a   (2572 kB)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3990.39 BogoMIPS (lpj=7980796)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Security Framework initialized
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] SELinux:  Disabled at boot.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] AppArmor: AppArmor initialized
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Mount-cache hash table entries: 512
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Initializing cgroup subsys ns
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Initializing cgroup subsys cpuacct
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Initializing cgroup subsys memory
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: Processor Core ID: 0
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] using mwait in idle threads.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Checking 'hlt' instruction... OK.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.017684] ACPI: Core revision 20080609
Jan 13 16:25:23 Kesre-laptop kernel: [    0.020616] ACPI: Checking initramfs for custom DSDT
Jan 13 16:25:23 Kesre-laptop kernel: [    0.328246] ENABLING IO-APIC IRQs
Jan 13 16:25:23 Kesre-laptop kernel: [    0.328436] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan 13 16:25:23 Kesre-laptop kernel: [    0.368749] CPU0: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
Jan 13 16:25:23 Kesre-laptop kernel: [    0.372023] Booting processor 1/1 ip 6000
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Initializing CPU#1
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] Calibrating delay using timer specific routine.. 3990.45 BogoMIPS (lpj=7980913)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: L2 cache: 2048K
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: Physical Processor ID: 0
Jan 13 16:25:23 Kesre-laptop kernel: [    0.004000] CPU: Processor Core ID: 1
Jan 13 16:25:23 Kesre-laptop kernel: [    0.456483] CPU1: Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz stepping 0d
Jan 13 16:25:23 Kesre-laptop kernel: [    0.456500] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460047] Brought up 2 CPUs
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460050] Total of 2 processors activated (7980.85 BogoMIPS).
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460159] net_namespace: 840 bytes
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460159] Booting paravirtualized kernel on bare hardware
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460290] Time: 16:24:56  Date: 01/13/09
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460315] NET: Registered protocol family 16
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460333] EISA bus registered
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460333] ACPI: bus type pci registered
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460333] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460333] PCI: MCFG area at e0000000 reserved in E820
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460333] PCI: Using MMCONFIG for extended config space
Jan 13 16:25:23 Kesre-laptop kernel: [    0.460333] PCI: Using configuration type 1 for base access
Jan 13 16:25:23 Kesre-laptop kernel: [    0.467305] ACPI: BIOS _OSI(Linux) query ignored via DMI
Jan 13 16:25:23 Kesre-laptop kernel: [    0.468558] ACPI: Interpreter enabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.468561] ACPI: (supports S0 S3 S4 S5)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.468577] ACPI: Using IOAPIC for interrupt routing
Jan 13 16:25:23 Kesre-laptop kernel: [    0.468638] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496362] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496362] ACPI: EC: driver started in interrupt mode
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496362] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496459] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496466] pci 0000:00:1a.7: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496572] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496577] pci 0000:00:1b.0: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496651] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496656] pci 0000:00:1c.0: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496731] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496736] pci 0000:00:1c.1: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496814] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.496819] pci 0000:00:1c.5: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.497132] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.497138] pci 0000:00:1d.7: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.497303] pci 0000:00:1f.0: quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jan 13 16:25:23 Kesre-laptop kernel: [    0.497307] pci 0000:00:1f.0: quirk: region 1180-11bf claimed by ICH6 GPIO
Jan 13 16:25:23 Kesre-laptop kernel: [    0.497521] pci 0000:00:1f.2: PME# supported from D3hot
Jan 13 16:25:23 Kesre-laptop kernel: [    0.497527] pci 0000:00:1f.2: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.498021] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.498034] pci 0000:02:00.0: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500319] pci 0000:06:00.0: PME# supported from D1 D2 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500326] pci 0000:06:00.0: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500516] pci 0000:07:09.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500522] pci 0000:07:09.0: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500624] pci 0000:07:09.1: PME# supported from D0 D1 D2 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500629] pci 0000:07:09.1: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500732] pci 0000:07:09.2: PME# supported from D0 D1 D2 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500738] pci 0000:07:09.2: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500840] pci 0000:07:09.3: PME# supported from D0 D1 D2 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500845] pci 0000:07:09.3: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500949] pci 0000:07:09.4: PME# supported from D0 D1 D2 D3hot D3cold
Jan 13 16:25:23 Kesre-laptop kernel: [    0.500954] pci 0000:07:09.4: PME# disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.501003] pci 0000:00:1e.0: transparent bridge
Jan 13 16:25:23 Kesre-laptop kernel: [    0.512615] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.512615] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan 13 16:25:23 Kesre-laptop kernel: [    0.512615] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.512615] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan 13 16:25:23 Kesre-laptop kernel: [    0.512687] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jan 13 16:25:23 Kesre-laptop kernel: [    0.512818] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.512952] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jan 13 16:25:23 Kesre-laptop kernel: [    0.513084] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jan 13 16:25:23 Kesre-laptop kernel: [    0.513162] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan 13 16:25:23 Kesre-laptop kernel: [    0.513162] pnp: PnP ACPI init
Jan 13 16:25:23 Kesre-laptop kernel: [    0.513162] ACPI: bus type pnp registered
Jan 13 16:25:23 Kesre-laptop kernel: [    0.516774] pnp: PnP ACPI: found 11 devices
Jan 13 16:25:23 Kesre-laptop kernel: [    0.516774] ACPI: ACPI bus type pnp unregistered
Jan 13 16:25:23 Kesre-laptop kernel: [    0.516774] PnPBIOS: Disabled by ACPI PNP
Jan 13 16:25:23 Kesre-laptop kernel: [    0.516774] PCI: Using ACPI for IRQ routing
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524042] NET: Registered protocol family 8
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524045] NET: Registered protocol family 20
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524060] NetLabel: Initializing
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524060] NetLabel:  domain hash size = 128
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524060] NetLabel:  protocols = UNLABELED CIPSOv4
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524063] NetLabel:  unlabeled traffic allowed by default
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524070] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jan 13 16:25:23 Kesre-laptop kernel: [    0.524075] hpet0: 3 64-bit timers, 14318180 Hz
Jan 13 16:25:23 Kesre-laptop kernel: [    0.525558] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan 13 16:25:23 Kesre-laptop kernel: [    0.525561]    actual entries 65620
Jan 13 16:25:23 Kesre-laptop kernel: [    0.525650] AppArmor: AppArmor Filesystem Enabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.525679] ACPI: RTC can wake from S4
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532021] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532024] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532027] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532030] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532033] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532036] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532039] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532042] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532053] system 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532060] system 00:06: ioport range 0x380-0x383 has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532063] system 00:06: ioport range 0x680-0x69f has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532066] system 00:06: ioport range 0x800-0x80f has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532069] system 00:06: ioport range 0x1000-0x107f has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532072] system 00:06: ioport range 0x1180-0x11bf has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532075] system 00:06: ioport range 0x1640-0x164f has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532078] system 00:06: ioport range 0xfe00-0xfe00 has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532084] system 00:07: ioport range 0x6a0-0x6af has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.532087] system 00:07: ioport range 0x6b0-0x6ff has been reserved
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567203] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567207] pci 0000:00:1c.0:   IO window: 0x4000-0x7fff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567214] pci 0000:00:1c.0:   MEM window: 0xf4000000-0xf7ffffff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567219] pci 0000:00:1c.0:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567228] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567232] pci 0000:00:1c.1:   IO window: 0x8000-0xbfff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567239] pci 0000:00:1c.1:   MEM window: 0xc0000000-0xc3ffffff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567244] pci 0000:00:1c.1:   PREFETCH window: 0x000000c8000000-0x000000cbffffff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567253] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:06
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567257] pci 0000:00:1c.5:   IO window: 0xc000-0xcfff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567263] pci 0000:00:1c.5:   MEM window: 0xf8200000-0xf82fffff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567268] pci 0000:00:1c.5:   PREFETCH window: 0x00000088000000-0x000000880fffff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567277] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567279] pci 0000:00:1e.0:   IO window: disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567286] pci 0000:00:1e.0:   MEM window: 0xf8300000-0xf83fffff
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567291] pci 0000:00:1e.0:   PREFETCH window: disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567310] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567326] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567341] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567360] bus: 00 index 0 io port: [0, ffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567362] bus: 00 index 1 mmio: [0, ffffffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567364] bus: 02 index 0 io port: [4000, 7fff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567366] bus: 02 index 1 mmio: [f4000000, f7ffffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567368] bus: 02 index 2 mmio: [f0000000, f3ffffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567370] bus: 02 index 3 mmio: [0, 0]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567372] bus: 04 index 0 io port: [8000, bfff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567374] bus: 04 index 1 mmio: [c0000000, c3ffffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567376] bus: 04 index 2 mmio: [c8000000, cbffffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567378] bus: 04 index 3 mmio: [0, 0]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567380] bus: 06 index 0 io port: [c000, cfff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567382] bus: 06 index 1 mmio: [f8200000, f82fffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567384] bus: 06 index 2 mmio: [88000000, 880fffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567386] bus: 06 index 3 mmio: [0, 0]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567388] bus: 07 index 0 mmio: [0, 0]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567390] bus: 07 index 1 mmio: [f8300000, f83fffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567392] bus: 07 index 2 mmio: [0, 0]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567394] bus: 07 index 3 io port: [0, ffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567396] bus: 07 index 4 mmio: [0, ffffffff]
Jan 13 16:25:23 Kesre-laptop kernel: [    0.567404] NET: Registered protocol family 2
Jan 13 16:25:23 Kesre-laptop kernel: [    0.580047] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.580271] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.580608] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.580786] TCP: Hash tables configured (established 131072 bind 65536)
Jan 13 16:25:23 Kesre-laptop kernel: [    0.580789] TCP reno registered
Jan 13 16:25:23 Kesre-laptop kernel: [    0.584069] NET: Registered protocol family 1
Jan 13 16:25:23 Kesre-laptop kernel: [    0.584180] checking if image is initramfs... it is
Jan 13 16:25:23 Kesre-laptop kernel: [    1.267601] Freeing initrd memory: 8001k freed
Jan 13 16:25:23 Kesre-laptop kernel: [    1.267774] Simple Boot Flag at 0x35 set to 0x1
Jan 13 16:25:23 Kesre-laptop kernel: [    1.268718] audit: initializing netlink socket (disabled)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.268740] type=2000 audit(1231863896.268:1): initialized
Jan 13 16:25:23 Kesre-laptop kernel: [    1.274604] highmem bounce pool size: 64 pages
Jan 13 16:25:23 Kesre-laptop kernel: [    1.274610] HugeTLB registered 4 MB page size, pre-allocated 0 pages
Jan 13 16:25:23 Kesre-laptop kernel: [    1.276887] VFS: Disk quotas dquot_6.5.1
Jan 13 16:25:23 Kesre-laptop kernel: [    1.276972] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.277074] msgmni has been set to 1743
Jan 13 16:25:23 Kesre-laptop kernel: [    1.277190] io scheduler noop registered
Jan 13 16:25:23 Kesre-laptop kernel: [    1.277193] io scheduler anticipatory registered
Jan 13 16:25:23 Kesre-laptop kernel: [    1.277195] io scheduler deadline registered
Jan 13 16:25:23 Kesre-laptop kernel: [    1.277207] io scheduler cfq registered (default)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.277530] pcieport-driver 0000:00:1c.0: found MSI capability
Jan 13 16:25:23 Kesre-laptop kernel: [    1.277827] pcieport-driver 0000:00:1c.1: found MSI capability
Jan 13 16:25:23 Kesre-laptop kernel: [    1.278113] pcieport-driver 0000:00:1c.5: found MSI capability
Jan 13 16:25:23 Kesre-laptop kernel: [    1.278573] isapnp: Scanning for PnP cards...
Jan 13 16:25:23 Kesre-laptop kernel: [    1.632662] isapnp: No Plug & Play device found
Jan 13 16:25:23 Kesre-laptop kernel: [    1.664894] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan 13 16:25:23 Kesre-laptop kernel: [    1.667046] brd: module loaded
Jan 13 16:25:23 Kesre-laptop kernel: [    1.667112] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan 13 16:25:23 Kesre-laptop kernel: [    1.667233] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jan 13 16:25:23 Kesre-laptop kernel: [    1.708216] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan 13 16:25:23 Kesre-laptop kernel: [    1.708222] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan 13 16:25:23 Kesre-laptop kernel: [    1.708435] mice: PS/2 mouse device common for all mice
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711417] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711448] rtc0: alarms up to one month, y3k, hpet irqs
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711573] EISA: Probing bus 0 at eisa.0
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711580] Cannot allocate resource for EISA slot 1
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711591] Cannot allocate resource for EISA slot 4
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711594] Cannot allocate resource for EISA slot 5
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711596] Cannot allocate resource for EISA slot 6
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711598] Cannot allocate resource for EISA slot 7
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711600] Cannot allocate resource for EISA slot 8
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711602] EISA: Detected 0 cards.
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711605] cpuidle: using governor ladder
Jan 13 16:25:23 Kesre-laptop kernel: [    1.711608] cpuidle: using governor menu
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712112] TCP cubic registered
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712137] Using IPI No-Shortcut mode
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712300] registered taskstats version 1
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712432]   Magic number: 9:17:439
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712490] pcieport-driver 0000:00:1c.0: hash matches
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712534] rtc_cmos 00:08: setting system clock to 2009-01-13 16:24:57 UTC (1231863897)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712537] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712539] EDD information not available.
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712769] Freeing unused kernel memory: 424k freed
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712805] Write protecting the kernel text: 2576k
Jan 13 16:25:23 Kesre-laptop kernel: [    1.712831] Write protecting the kernel read-only data: 936k
Jan 13 16:25:23 Kesre-laptop kernel: [    1.740469] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan 13 16:25:23 Kesre-laptop kernel: [    1.865998] fuse init (API version 7.9)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.888066] ACPI: SSDT 7F6D6998, 027A (r1  HP    30CC         3000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.888515] ACPI: SSDT 7F6D6329, 05EA (r1  HP    30CC         3001 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.891196] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jan 13 16:25:23 Kesre-laptop kernel: [    1.891253] processor ACPI0007:00: registered as cooling_device0
Jan 13 16:25:23 Kesre-laptop kernel: [    1.891257] ACPI: Processor [CPU0] (supports 8 throttling states)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.891624] ACPI: SSDT 7F6D6C12, 00C8 (r1  HP    30CC         3000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.892027] ACPI: SSDT 7F6D6913, 0085 (r1  HP    30CC         3000 INTL 20061109)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.893162] Marking TSC unstable due to TSC halts in idle
Jan 13 16:25:23 Kesre-laptop kernel: [    1.893244] ACPI: CPU1 (power states: C1[C1] C2[C2])
Jan 13 16:25:23 Kesre-laptop kernel: [    1.893294] processor ACPI0007:01: registered as cooling_device1
Jan 13 16:25:23 Kesre-laptop kernel: [    1.893298] ACPI: Processor [CPU1] (supports 8 throttling states)
Jan 13 16:25:23 Kesre-laptop kernel: [    1.896091] ACPI Exception (thermal-0377): AE_OK, No or invalid critical threshold [20080609]
Jan 13 16:25:23 Kesre-laptop kernel: [    2.232742] usbcore: registered new interface driver usbfs
Jan 13 16:25:23 Kesre-laptop kernel: [    2.232765] usbcore: registered new interface driver hub
Jan 13 16:25:23 Kesre-laptop kernel: [    2.232821] usbcore: registered new device driver usb
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244310] USB Universal Host Controller Interface driver v3.0
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244356] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244374] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244414] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244462] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244608] usb usb1: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244635] hub 1-0:1.0: USB hub found
Jan 13 16:25:23 Kesre-laptop kernel: [    2.244641] hub 1-0:1.0: 2 ports detected
Jan 13 16:25:23 Kesre-laptop kernel: [    2.348276] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 13 16:25:23 Kesre-laptop kernel: [    2.348290] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jan 13 16:25:23 Kesre-laptop kernel: [    2.348319] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Jan 13 16:25:23 Kesre-laptop kernel: [    2.348357] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
Jan 13 16:25:23 Kesre-laptop kernel: [    2.348448] usb usb2: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    2.348475] hub 2-0:1.0: USB hub found
Jan 13 16:25:23 Kesre-laptop kernel: [    2.348482] hub 2-0:1.0: 2 ports detected
Jan 13 16:25:23 Kesre-laptop kernel: [    2.366229] No dock devices found.
Jan 13 16:25:23 Kesre-laptop kernel: [    2.382205] SCSI subsystem initialized
Jan 13 16:25:23 Kesre-laptop kernel: [    2.452433] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 13 16:25:23 Kesre-laptop kernel: [    2.452454] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jan 13 16:25:23 Kesre-laptop kernel: [    2.452483] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
Jan 13 16:25:23 Kesre-laptop kernel: [    2.456401] ehci_hcd 0000:00:1a.7: debug port 1
Jan 13 16:25:23 Kesre-laptop kernel: [    2.456424] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8604800
Jan 13 16:25:23 Kesre-laptop kernel: [    2.473017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 13 16:25:23 Kesre-laptop kernel: [    2.473134] usb usb3: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    2.473162] hub 3-0:1.0: USB hub found
Jan 13 16:25:23 Kesre-laptop kernel: [    2.473170] hub 3-0:1.0: 4 ports detected
Jan 13 16:25:23 Kesre-laptop kernel: [    2.577412] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 13 16:25:23 Kesre-laptop kernel: [    2.577429] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jan 13 16:25:23 Kesre-laptop kernel: [    2.577456] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Jan 13 16:25:23 Kesre-laptop kernel: [    2.577495] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001860
Jan 13 16:25:23 Kesre-laptop kernel: [    2.577589] usb usb4: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    2.577615] hub 4-0:1.0: USB hub found
Jan 13 16:25:23 Kesre-laptop kernel: [    2.577623] hub 4-0:1.0: 2 ports detected
Jan 13 16:25:23 Kesre-laptop kernel: [    2.681630] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 13 16:25:23 Kesre-laptop kernel: [    2.681645] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jan 13 16:25:23 Kesre-laptop kernel: [    2.681671] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Jan 13 16:25:23 Kesre-laptop kernel: [    2.681709] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
Jan 13 16:25:23 Kesre-laptop kernel: [    2.681805] usb usb5: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    2.681831] hub 5-0:1.0: USB hub found
Jan 13 16:25:23 Kesre-laptop kernel: [    2.681838] hub 5-0:1.0: 2 ports detected
Jan 13 16:25:23 Kesre-laptop kernel: [    2.785318] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
Jan 13 16:25:23 Kesre-laptop kernel: [    2.785333] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jan 13 16:25:23 Kesre-laptop kernel: [    2.785361] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Jan 13 16:25:23 Kesre-laptop kernel: [    2.785393] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
Jan 13 16:25:23 Kesre-laptop kernel: [    2.785490] usb usb6: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    2.785517] hub 6-0:1.0: USB hub found
Jan 13 16:25:23 Kesre-laptop kernel: [    2.785523] hub 6-0:1.0: 2 ports detected
Jan 13 16:25:23 Kesre-laptop kernel: [    2.992320] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
Jan 13 16:25:23 Kesre-laptop kernel: [    2.992339] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jan 13 16:25:23 Kesre-laptop kernel: [    2.992369] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Jan 13 16:25:23 Kesre-laptop kernel: [    2.996283] ehci_hcd 0000:00:1d.7: debug port 1
Jan 13 16:25:23 Kesre-laptop kernel: [    2.996295] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8604c00
Jan 13 16:25:23 Kesre-laptop kernel: [    3.008026] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jan 13 16:25:23 Kesre-laptop kernel: [    3.008107] usb usb7: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    3.008133] hub 7-0:1.0: USB hub found
Jan 13 16:25:23 Kesre-laptop kernel: [    3.008140] hub 7-0:1.0: 6 ports detected
Jan 13 16:25:23 Kesre-laptop kernel: [    3.216473] pata_acpi 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan 13 16:25:23 Kesre-laptop kernel: [    3.216520] pata_acpi 0000:00:1f.1: PCI INT A disabled
Jan 13 16:25:23 Kesre-laptop kernel: [    3.216568] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Jan 13 16:25:23 Kesre-laptop kernel: [    3.216582] r8169 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jan 13 16:25:23 Kesre-laptop kernel: [    3.216981] eth0: RTL8101e at 0xf884c000, 00:1e:68:04:ee:13, XID 34200000 IRQ 220
Jan 13 16:25:23 Kesre-laptop kernel: [    3.217989] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218082] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218085] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218300] scsi0 : ahci
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218407] scsi1 : ahci
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218492] scsi2 : ahci
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218602] ata1: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604100 irq 219
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218605] ata2: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604180 irq 219
Jan 13 16:25:23 Kesre-laptop kernel: [    3.218608] ata3: SATA max UDMA/133 abar m2048@0xf8604000 port 0xf8604200 irq 219
Jan 13 16:25:23 Kesre-laptop kernel: [    3.536057] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jan 13 16:25:23 Kesre-laptop kernel: [    3.536665] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Jan 13 16:25:23 Kesre-laptop kernel: [    3.536670] ata1.00: ATA-7: WDC WD1600BEVS-60RST0, 04.01G04, max UDMA/100
Jan 13 16:25:23 Kesre-laptop kernel: [    3.536673] ata1.00: 312581808 sectors, multi 16: LBA48 
Jan 13 16:25:23 Kesre-laptop kernel: [    3.537321] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 filtered out
Jan 13 16:25:23 Kesre-laptop kernel: [    3.537333] ata1.00: configured for UDMA/100
Jan 13 16:25:23 Kesre-laptop kernel: [    3.616033] usb 6-2: new full speed USB device using uhci_hcd and address 2
Jan 13 16:25:23 Kesre-laptop kernel: [    3.788766] usb 6-2: configuration #1 chosen from 1 choice
Jan 13 16:25:23 Kesre-laptop kernel: [    3.872059] ata2: SATA link down (SStatus 0 SControl 300)
Jan 13 16:25:23 Kesre-laptop kernel: [    4.212053] ata3: SATA link down (SStatus 0 SControl 300)
Jan 13 16:25:23 Kesre-laptop kernel: [    4.228152] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-6 04.0 PQ: 0 ANSI: 5
Jan 13 16:25:23 Kesre-laptop kernel: [    4.228270] ohci1394 0000:07:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jan 13 16:25:23 Kesre-laptop kernel: [    4.280971] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[20]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
Jan 13 16:25:23 Kesre-laptop kernel: [    4.290896] ata_piix 0000:00:1f.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jan 13 16:25:23 Kesre-laptop kernel: [    4.291678] scsi3 : ata_piix
Jan 13 16:25:23 Kesre-laptop kernel: [    4.291759] scsi4 : ata_piix
Jan 13 16:25:23 Kesre-laptop kernel: [    4.292487] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
Jan 13 16:25:23 Kesre-laptop kernel: [    4.292491] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
Jan 13 16:25:23 Kesre-laptop kernel: [    4.298667] scsi 0:0:0:0: Attached scsi generic sg0 type 0
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312105] Driver 'sd' needs updating - please use bus_type methods
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312215] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312235] sd 0:0:0:0: [sda] Write Protect is off
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312271] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312343] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312362] sd 0:0:0:0: [sda] Write Protect is off
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312398] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jan 13 16:25:23 Kesre-laptop kernel: [    4.312402]  sda: sda1 sda2 < sda5 > sda3
Jan 13 16:25:23 Kesre-laptop kernel: [    4.380236] sd 0:0:0:0: [sda] Attached SCSI disk
Jan 13 16:25:23 Kesre-laptop kernel: [    4.468460] ata4.00: ATAPI: TSSTcorp CDDVDW TS-L632N, 0503, max MWDMA2
Jan 13 16:25:23 Kesre-laptop kernel: [    4.500408] ata4.00: configured for MWDMA2
Jan 13 16:25:23 Kesre-laptop kernel: [    4.670642] scsi 3:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632N  0503 PQ: 0 ANSI: 5
Jan 13 16:25:23 Kesre-laptop kernel: [    4.670777] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Jan 13 16:25:23 Kesre-laptop kernel: [    4.701413] Driver 'sr' needs updating - please use bus_type methods
Jan 13 16:25:23 Kesre-laptop kernel: [    4.717954] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jan 13 16:25:23 Kesre-laptop kernel: [    4.717958] Uniform CD-ROM driver Revision: 3.20
Jan 13 16:25:23 Kesre-laptop kernel: [   10.042267] EXT3-fs: INFO: recovery required on readonly filesystem.
Jan 13 16:25:23 Kesre-laptop kernel: [   10.042271] EXT3-fs: write access will be enabled during recovery.
Jan 13 16:25:23 Kesre-laptop kernel: [   14.709465] kjournald starting.  Commit interval 5 seconds
Jan 13 16:25:23 Kesre-laptop kernel: [   14.709492] EXT3-fs: sda3: orphan cleanup on readonly fs
Jan 13 16:25:23 Kesre-laptop kernel: [   14.738201] EXT3-fs: sda3: 18 orphan inodes deleted
Jan 13 16:25:23 Kesre-laptop kernel: [   14.738203] EXT3-fs: recovery complete.
Jan 13 16:25:23 Kesre-laptop kernel: [   14.761901] EXT3-fs: mounted filesystem with ordered data mode.
Jan 13 16:25:23 Kesre-laptop kernel: [   21.960127] udevd version 124 started
Jan 13 16:25:23 Kesre-laptop kernel: [   22.427631] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan 13 16:25:23 Kesre-laptop kernel: [   22.467214] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan 13 16:25:23 Kesre-laptop kernel: [   22.515517] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jan 13 16:25:23 Kesre-laptop kernel: [   22.557754] Linux agpgart interface v0.103
Jan 13 16:25:23 Kesre-laptop kernel: [   22.601501] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
Jan 13 16:25:23 Kesre-laptop kernel: [   22.601975] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
Jan 13 16:25:23 Kesre-laptop kernel: [   22.616469] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
Jan 13 16:25:23 Kesre-laptop kernel: [   22.715224] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan 13 16:25:23 Kesre-laptop kernel: [   22.751831] ACPI: Power Button (FF) [PWRF]
Jan 13 16:25:23 Kesre-laptop kernel: [   22.752011] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input4
Jan 13 16:25:23 Kesre-laptop kernel: [   22.781030] ACPI: Power Button (CM) [PWRB]
Jan 13 16:25:23 Kesre-laptop kernel: [   22.781166] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input5
Jan 13 16:25:23 Kesre-laptop kernel: [   22.813023] ACPI: Sleep Button (CM) [SLPB]
Jan 13 16:25:23 Kesre-laptop kernel: [   22.813896] ACPI: AC Adapter [ACAD] (on-line)
Jan 13 16:25:23 Kesre-laptop kernel: [   22.814003] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input6
Jan 13 16:25:23 Kesre-laptop kernel: [   22.815119] ACPI: Lid Switch [LID]
Jan 13 16:25:23 Kesre-laptop kernel: [   22.844368] iTCO_vendor_support: vendor-support=0
Jan 13 16:25:23 Kesre-laptop kernel: [   22.865668] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.03 (30-Apr-2008)
Jan 13 16:25:23 Kesre-laptop kernel: [   22.865995] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
Jan 13 16:25:23 Kesre-laptop kernel: [   22.866139] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jan 13 16:25:23 Kesre-laptop kernel: [   22.908408] ACPI: Battery Slot [BAT0] (battery present)
Jan 13 16:25:23 Kesre-laptop kernel: [   22.908802] ACPI: WMI: Mapper loaded
Jan 13 16:25:23 Kesre-laptop kernel: [   22.936510] ricoh-mmc: Ricoh MMC Controller disabling driver
Jan 13 16:25:23 Kesre-laptop kernel: [   22.936513] ricoh-mmc: Copyright(c) Philip Langdale
Jan 13 16:25:23 Kesre-laptop kernel: [   22.936554] ricoh-mmc: Ricoh MMC controller found at 0000:07:09.2 [1180:0843] (rev 12)
Jan 13 16:25:23 Kesre-laptop kernel: [   22.936577] ricoh-mmc: Controller is now disabled.
Jan 13 16:25:23 Kesre-laptop kernel: [   23.084944] sdhci: Secure Digital Host Controller Interface driver
Jan 13 16:25:23 Kesre-laptop kernel: [   23.084947] sdhci: Copyright(c) Pierre Ossman
Jan 13 16:25:23 Kesre-laptop kernel: [   23.162506] sdhci-pci 0000:07:09.1: SDHCI controller found [1180:0822] (rev 22)
Jan 13 16:25:23 Kesre-laptop kernel: [   23.162524] sdhci-pci 0000:07:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Jan 13 16:25:23 Kesre-laptop kernel: [   23.165612] mmc0: SDHCI controller on PCI [0000:07:09.1] using PIO
Jan 13 16:25:23 Kesre-laptop kernel: [   23.258670] acpi device:06: registered as cooling_device2
Jan 13 16:25:23 Kesre-laptop kernel: [   23.258886] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/device:03/input/input7
Jan 13 16:25:23 Kesre-laptop kernel: [   23.284025] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jan 13 16:25:23 Kesre-laptop kernel: [   23.287182] acpi device:0b: registered as cooling_device3
Jan 13 16:25:23 Kesre-laptop kernel: [   23.287571] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:08/input/input8
Jan 13 16:25:23 Kesre-laptop kernel: [   23.316045] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
Jan 13 16:25:23 Kesre-laptop kernel: [   23.608715] Bluetooth: Core ver 2.13
Jan 13 16:25:23 Kesre-laptop kernel: [   23.632069] NET: Registered protocol family 31
Jan 13 16:25:23 Kesre-laptop kernel: [   23.632070] Bluetooth: HCI device and connection manager initialized
Jan 13 16:25:23 Kesre-laptop kernel: [   23.632074] Bluetooth: HCI socket layer initialized
Jan 13 16:25:23 Kesre-laptop kernel: [   23.727214] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
Jan 13 16:25:23 Kesre-laptop kernel: [   23.727218] iwl3945: Copyright(c) 2003-2008 Intel Corporation
Jan 13 16:25:23 Kesre-laptop kernel: [   23.727333] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 13 16:25:23 Kesre-laptop kernel: [   23.727369] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
Jan 13 16:25:23 Kesre-laptop kernel: [   23.842649] Bluetooth: Generic Bluetooth USB driver ver 0.3
Jan 13 16:25:23 Kesre-laptop kernel: [   23.842752] usbcore: registered new interface driver btusb
Jan 13 16:25:23 Kesre-laptop kernel: [   23.860052] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
Jan 13 16:25:23 Kesre-laptop kernel: [   24.146773] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
Jan 13 16:25:23 Kesre-laptop kernel: [   24.253928] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
Jan 13 16:25:23 Kesre-laptop kernel: [   24.289649] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
Jan 13 16:25:23 Kesre-laptop kernel: [   24.291689] iwl3945 0000:02:00.0: PCI INT A disabled
Jan 13 16:25:23 Kesre-laptop kernel: [   24.920729] lp: driver loaded but no devices found
Jan 13 16:25:23 Kesre-laptop kernel: [   25.431079] EXT3 FS on sda3, internal journal
Jan 13 16:25:23 Kesre-laptop kernel: [   26.021000] type=1505 audit(1231892722.222:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4316
Jan 13 16:25:23 Kesre-laptop kernel: [   26.171296] type=1505 audit(1231892722.371:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4321
Jan 13 16:25:23 Kesre-laptop kernel: [   26.171499] type=1505 audit(1231892722.371:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4321
Jan 13 16:25:23 Kesre-laptop kernel: [   26.279501] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan 13 16:25:23 Kesre-laptop kernel: [   27.734416] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
Jan 13 16:25:23 Kesre-laptop kernel: [   27.798700] apm: BIOS not found.
Jan 13 16:25:24 Kesre-laptop kernel: [   27.953892] ppdev: user-space parallel port driver
Jan 13 16:25:26 Kesre-laptop kernel: [   30.157600] Bluetooth: L2CAP ver 2.11
Jan 13 16:25:26 Kesre-laptop kernel: [   30.157609] Bluetooth: L2CAP socket layer initialized
Jan 13 16:25:26 Kesre-laptop kernel: [   30.178086] Bluetooth: SCO (Voice Link) ver 0.6
Jan 13 16:25:26 Kesre-laptop kernel: [   30.178097] Bluetooth: SCO socket layer initialized
Jan 13 16:25:26 Kesre-laptop kernel: [   30.206988] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 13 16:25:26 Kesre-laptop kernel: [   30.206993] Bluetooth: BNEP filters: protocol multicast
Jan 13 16:25:26 Kesre-laptop kernel: [   30.227813] Bridge firewalling registered
Jan 13 16:25:26 Kesre-laptop kernel: [   30.362920] Bluetooth: RFCOMM socket layer initialized
Jan 13 16:25:26 Kesre-laptop kernel: [   30.363766] Bluetooth: RFCOMM TTY layer initialized
Jan 13 16:25:26 Kesre-laptop kernel: [   30.363771] Bluetooth: RFCOMM ver 1.10
Jan 13 16:25:29 Kesre-laptop kernel: [   33.718523] [drm] Initialized drm 1.1.0 20060810
Jan 13 16:25:29 Kesre-laptop kernel: [   33.727934] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 13 16:25:29 Kesre-laptop kernel: [   33.728271] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jan 13 16:25:30 Kesre-laptop kernel: [   34.456510] r8169: eth0: link down
Jan 13 16:25:30 Kesre-laptop kernel: [   34.458201] iwl3945 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 13 16:25:30 Kesre-laptop kernel: [   34.458620] firmware: requesting iwlwifi-3945-1.ucode
Jan 13 16:25:30 Kesre-laptop kernel: [   34.604724] Registered led device: iwl-phy0:radio
Jan 13 16:25:30 Kesre-laptop kernel: [   34.604814] Registered led device: iwl-phy0:assoc
Jan 13 16:25:30 Kesre-laptop kernel: [   34.604855] Registered led device: iwl-phy0:RX
Jan 13 16:25:30 Kesre-laptop kernel: [   34.604902] Registered led device: iwl-phy0:TX
Jan 13 16:25:31 Kesre-laptop kernel: [   34.801948] NET: Registered protocol family 17
Jan 13 16:25:43 Kesre-laptop pulseaudio[5615]: ltdl-bind-now.c: Failed to find original dlopen loader.
Jan 13 16:25:43 Kesre-laptop pulseaudio[5617]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Jan 13 16:25:43 Kesre-laptop pulseaudio[5617]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Jan 13 16:26:25 Kesre-laptop kernel: [   88.808747] NET: Registered protocol family 10
Jan 13 16:26:25 Kesre-laptop kernel: [   88.810344] lo: Disabled Privacy Extensions
Jan 13 16:26:25 Kesre-laptop kernel: [   88.811835] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 13 16:45:27 Kesre-laptop -- MARK --
Jan 13 17:05:27 Kesre-laptop -- MARK --
Jan 13 17:25:27 Kesre-laptop -- MARK --
Jan 13 17:31:02 Kesre-laptop kernel: [ 3962.705896] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
Jan 13 17:31:02 Kesre-laptop kernel: [ 3962.705910] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
Jan 13 17:31:21 Kesre-laptop kernel: [ 3981.521912] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
Jan 13 17:31:22 Kesre-laptop kernel: [ 3982.042694] psmouse.c: resync failed, issuing reconnect request
Jan 13 17:31:23 Kesre-laptop kernel: [ 3983.701298] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04713/0x200000
Jan 13 17:31:23 Kesre-laptop kernel: [ 3983.808410] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
Jan 13 17:45:27 Kesre-laptop -- MARK --
Jan 13 18:05:27 Kesre-laptop -- MARK --
Jan 13 18:25:27 Kesre-laptop -- MARK --
Jan 13 18:45:27 Kesre-laptop -- MARK --
Jan 13 19:05:27 Kesre-laptop -- MARK --
Jan 13 19:12:37 Kesre-laptop kernel: [10057.553052] CE: hpet increasing min_delta_ns to 15000 nsec
Jan 13 19:25:27 Kesre-laptop -- MARK --
Jan 13 19:45:27 Kesre-laptop -- MARK --
Jan 13 20:05:27 Kesre-laptop -- MARK --
Jan 13 20:25:27 Kesre-laptop -- MARK --
Jan 13 20:26:21 Kesre-laptop kernel: [14480.985842] UDF-fs: No VRS found
Jan 13 20:45:27 Kesre-laptop -- MARK --
```


so the thing that said "last message repeated xxxx times"

could that be whats causing the crashes?

also, theres a reference to a magic number and then the "No VRS found"

---

### Post by AlexSIR on 2009-01-27
Hi!
Check your the **/boot/grub/menu.lst** file
Has it **initrd** line?
For example:
*initrd          /boot/initrd.img-2.6.27-7-generic*

I had the same problem after update my Ubuntu, and [[COLOR="Blue"]_this blog_[/COLOR]]("http://www.maxhorvath.com/2008/11/problems-when-upgrading-to-ubuntu-810-kernel-panic-unable-to-mount-root-fs.html") has helped me with it.

---

### Post by kesre on 2009-01-27
hmm

I do have it - it looks like the same format as the working kernel..
and the img file is at the location it directs to

Does it need to be init.rd or just initrd ? (currently its initrd)

thanks for trying :D

---

### Post by AlexSIR on 2009-01-27
> **kesre said:**
> 
Does it need to be init.rd or just initrd ? (currently its initrd)

thanks for trying :D

Oh.. Of course I meant the line with **initrd **of the **/boot/grub/menu.lst** file (about the **/boot/initrd.img-2.6.2x-x-generic** file).
:)

---

### Post by Nicram on 2009-01-28
Well, for me kernel 2.6.27-11 is working now.
There is no need to use the older 2.6.27-10
It just happend, probably after some updates.
Check if it's working for you too.

---

### Post by AlexSIR on 2009-01-28
For me kernel 2.6.27-11 is working too!

---

### Post by Epilonsama on 2009-02-20
I have been reading this, but it seems my problem isn't solved.
I'm using linux mint, also this is a clean install, I'm  cant acces linux, so I cant use any command from linux.
I'm on my windows partition, but I have access to my linux partition.
Heres my grub menu.lst
> 
title		Linux Mint 6, kernel 2.6.27-7-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Linux Mint 6, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/sda5 ro single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Linux Mint 6, kernel Last successful boot
root		(hd0,4)
kernel		/boot/last-good-boot/vmlinuz root=/dev/sda5 ro quiet splash  last-good-boot
quiet

title		Linux Mint 6, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Also i haven't install any kernel that I remember, also I have a peculiar bug where the boot folder repeats itself lot of times or something, don't know if this is related.
Heres the bug(keep in mind its using windows address format):
X:\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot\boot

at this final boot it Vista says unspecified

---

### Post by sandrocchio_0.1 on 2009-06-08
Hello everybody.
I am afraid to report the same error with same circumstances. Fortunately the trick of using a previous kernel worked and I currently working under 

Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009

_The kernel version which is having troubles is_
Linux version **2.6.27-14-generic** (buildd@palmer) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Wed Apr 15 18:59:16 UTC 2009 (Ubuntu 2.6.27-14.33-generic)


On the syslog I have the following messages

> 
Jun  8 15:21:00 athokos x-session-manager[6488]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed 
Jun  8 15:21:00 athokos x-session-manager[6488]: WARNING: Client '(null)' failed to reply before timeout 
Jun  8 15:21:00 athokos x-session-manager[6488]: CRITICAL: gsm_client_peek_app_id: assertion `GSM_IS_CLIENT (client)' failed 
Jun  8 15:21:00 athokos x-session-manager[6488]: CRITICAL: gsm_client_get_app_name: assertion `GSM_IS_CLIENT (client)' failed 
Jun  8 15:21:00 athokos x-session-manager[6488]: CRITICAL: gsm_client_peek_id: assertion `GSM_IS_CLIENT (client)' failed 
Jun  8 15:21:09 athokos vmnetBridge: RTM_NEWLINK: name:wlan0 index:4 flags:0x00001003 
Jun  8 15:21:09 athokos vmnetBridge: Can't remove interface wlan0 4 (does not exist). 
Jun  8 15:21:54 athokos init: tty4 main process (4597) killed by TERM signal
Jun  8 15:21:54 athokos init: tty5 main process (4598) killed by TERM signal
Jun  8 15:21:54 athokos init: tty2 main process (4603) killed by TERM signal
Jun  8 15:21:54 athokos init: tty3 main process (4604) killed by TERM signal
Jun  8 15:21:54 athokos init: tty6 main process (4605) killed by TERM signal
Jun  8 15:21:54 athokos init: tty1 main process (6221) killed by TERM signal
Jun  8 15:21:56 athokos kernel: [21020.615792] apm: BIOS not found.
Jun  8 15:22:01 athokos vmnetBridge: RTM_DELLINK: name:pan0 index:23 flags:0x00001002 
Jun  8 15:22:01 athokos vmnetBridge: Can't remove interface pan0 23 (does not exist). 
Jun  8 15:22:01 athokos bluetoothd[2738]: bridge pan0 removed
Jun  8 15:22:01 athokos bluetoothd[2738]: Stopping SDP server
Jun  8 15:22:01 athokos bluetoothd[2738]: Exit
Jun  8 15:22:01 athokos avahi-daemon[5024]: Got SIGTERM, quitting.
Jun  8 15:22:01 athokos avahi-daemon[5024]: Leaving mDNS multicast group on interface vmnet8.IPv4 with address 192.168.53.1.
Jun  8 15:22:01 athokos avahi-daemon[5024]: Leaving mDNS multicast group on interface vmnet1.IPv4 with address 172.16.91.1.
Jun  8 15:22:02 athokos exiting on signal 15
Jun  8 17:31:03 athokos syslogd 1.5.0#2ubuntu6: restart.
Jun  8 17:31:03 athokos kernel: Inspecting /boot/System.map-2.6.27-11-generic
Jun  8 17:31:04 athokos kernel: Cannot find map file.
Jun  8 17:31:04 athokos kernel: Loaded 52092 symbols from 101 modules.
Jun  8 17:31:04 athokos kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  8 17:31:04 athokos kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  8 17:31:04 athokos kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.27-11.31-generic)
Jun  8 17:31:04 athokos kernel: [    0.000000] BIOS-provided physical RAM map:
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 00000000000e3000 - 0000000000100000 (reserved)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007f7a0000 (usable)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 000000007f7a0000 - 000000007f7ae000 (ACPI data)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 000000007f7ae000 - 000000007f7f0000 (ACPI NVS)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 000000007f7f0000 - 000000007f800000 (reserved)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun  8 17:31:04 athokos kernel: [    0.000000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
Jun  8 17:31:04 athokos kernel: [    0.000000] DMI 2.4 present.
Jun  8 17:31:04 athokos kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
Jun  8 17:31:04 athokos kernel: [    0.000000] last_pfn = 0x7f7a0 max_arch_pfn = 0x100000
Jun  8 17:31:04 athokos kernel: [    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
Jun  8 17:31:04 athokos kernel: [    0.000000] RAMDISK: 3781c000 - 37fef269
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: RSDP 000F80E0, 0024 (r2 ACPIAM)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: XSDT 7F7A0100, 008C (r1 _ASUS_ Notebook  9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: FACP 7F7A0290, 00F4 (r3 A_M_I_ OEMFACP   9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: DSDT 7F7A0680, C125 (r1  U1E00 U1E00001        1 INTL 20051117)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: FACS 7F7AE000, 0040
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: APIC 7F7A0390, 005C (r1 A_M_I_ OEMAPIC   9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: MCFG 7F7A0430, 003C (r1 A_M_I_ OEMMCFG   9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: SLIC 7F7A0470, 0176 (r1 _ASUS_ Notebook  9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: DBGP 7F7A03F0, 0034 (r1 A_M_I_ OEMDBGP   9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: BOOT 7F7A05F0, 0028 (r1 A_M_I_ OEMBOOT   9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: ECDT 7F7A0620, 0054 (r1 A_M_I_ OEMECDT   9000707 MSFT       97)
Jun  8 17:31:04 athokos kernel: [    0.000000] ACPI: OEMB 7F7AE040, 0060 (r1 A_M_I_ AMI_OEM   9000707 MSFT       97)
from kernel
> 
Jun  8 14:44:39 athokos kernel: [18782.963918] rfcomm_tty_ioctl: TIOCGSERIAL is not supported
Jun  8 15:21:56 athokos kernel: [21020.615792] apm: BIOS not found.
Jun  8 17:31:03 athokos kernel: Inspecting /boot/System.map-2.6.27-11-generic
Jun  8 17:31:04 athokos kernel: Cannot find map file.
Jun  8 17:31:04 athokos kernel: Loaded 52092 symbols from 101 modules.
Jun  8 17:31:04 athokos kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun  8 17:31:04 athokos kernel: [    0.000000] Initializing cgroup subsys cpu
Jun  8 17:31:04 athokos kernel: [    0.000000] Linux version 2.6.27-11-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Wed Apr 1 20:57:48 UTC 2009 (Ubuntu 2.6.27-11.31-generic)
I am not a guru and personally I can't clearly understand if something has happened before shut down or during boot.

---

### Post by sandrocchio_0.1 on 2009-06-08
Still me.
One thing I didn't mention is a message during boot regarding a bad gzip image and magic numbers

---

### Post by gnuskool on 2009-07-01
SOLVED [here]("http://ubuntuforums.org/showthread.php?t=1047068")

---

