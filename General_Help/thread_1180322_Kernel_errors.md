---
title: "Kernel errors"
date: 2009-06-06
forum: General Help
---

### Post by Dr Zin on 2009-06-06
I have a dual boot system so, when I select the Kernel build that I want. It gives me ata1-4 fail. I would like to post the error, I can remember the command to give you that error message. 8.10 only gave me an memory error, I believe it was cap message. Now ata error it is causing my system to freeze or hang.

AMD 2 64
MSI k9a2 P
4 GB of ram

---

### Post by Crafty Kisses on 2009-06-06
There's a couple of logs that you could post that might give us some help:
```
dmesg
tail /var/log/messages
```

---

### Post by Dr Zin on 2009-06-07
ok he is the code```
drzin@dr_zin:~$ dmesg
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset     
[    0.000000] Initializing cgroup subsys cpu        
[    0.000000] Linux version 2.6.28-11-generic (buildd@crested) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 (Ubuntu 2.6.28-11.42-generic)                                                    
[    0.000000] Command line: root=UUID=3a675246-e744-4082-80d9-5fe63a63e862 ro quiet splash                          
[    0.000000] KERNEL supported cpus:                                                                                
[    0.000000]   Intel GenuineIntel                                                                                  
[    0.000000]   AMD AuthenticAMD                                                                                    
[    0.000000]   Centaur CentaurHauls                                                                                
[    0.000000] BIOS-provided physical RAM map:                                                                       
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)                                              
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)                                            
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)                                            
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffc0000 (usable)                                              
[    0.000000]  BIOS-e820: 00000000cffc0000 - 00000000cffce000 (ACPI data)                                           
[    0.000000]  BIOS-e820: 00000000cffce000 - 00000000cfff0000 (ACPI NVS)                                            
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000cfffe000 (reserved)                                            
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)                                            
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)                                              
[    0.000000] DMI present.                                                                                          
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.                                       
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x3ffffffff                                                        
[    0.000000] last_pfn = 0xcffc0 max_arch_pfn = 0x3ffffffff                                                         
[    0.000000] Scanning 0 areas for low memory corruption                                                            
[    0.000000] modified physical RAM map:                                                                            
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)                                             
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)                                               
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)                                             
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)                                             
[    0.000000]  modified: 0000000000100000 - 00000000cffc0000 (usable)                                               
[    0.000000]  modified: 00000000cffc0000 - 00000000cffce000 (ACPI data)                                            
[    0.000000]  modified: 00000000cffce000 - 00000000cfff0000 (ACPI NVS)                                             
[    0.000000]  modified: 00000000cfff0000 - 00000000cfffe000 (reserved)                                             
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)                                             
[    0.000000]  modified: 0000000100000000 - 0000000130000000 (usable)                                               
[    0.000000] init_memory_mapping: 0000000000000000-00000000cffc0000                                                
[    0.000000]  0000000000 - 00cfe00000 page 2M                                                                      
[    0.000000]  00cfe00000 - 00cffc0000 page 4k                                                                      
[    0.000000] kernel direct mapping tables up to cffc0000 @ 10000-16000                                             
[    0.000000] last_map_addr: cffc0000 end: cffc0000                                                                 
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000                                                
[    0.000000]  0100000000 - 0130000000 page 2M                                                                      
[    0.000000] kernel direct mapping tables up to 130000000 @ 14000-1a000                                            
[    0.000000] last_map_addr: 130000000 end: 130000000                                                               
[    0.000000] RAMDISK: 3785f000 - 37fef5e3                                                                          
[    0.000000] ACPI: RSDP 000F98D0, 0014 (r0 ACPIAM)                                                                 
[    0.000000] ACPI: RSDT CFFC0000, 0038 (r1 031208 RSDT1611 20080312 MSFT       97)                                 
[    0.000000] ACPI: FACP CFFC0200, 0084 (r2 031208 FACP1611 20080312 MSFT       97)                                 
[    0.000000] ACPI: DSDT CFFC0440, 6E9B (r1  1ADNC 1ADNC001        1 INTL 20051117)                                 
[    0.000000] ACPI: FACS CFFCE000, 0040                                                                             
[    0.000000] ACPI: APIC CFFC0390, 006C (r1 031208 APIC1611 20080312 MSFT       97)                                 
[    0.000000] ACPI: MCFG CFFC0400, 003C (r1 031208 OEMMCFG  20080312 MSFT       97)                                 
[    0.000000] ACPI: OEMB CFFCE040, 0071 (r1 031208 OEMB1611 20080312 MSFT       97)                                 
[    0.000000] ACPI: HPET CFFC72E0, 0038 (r1 031208 OEMHPET  20080312 MSFT       97)                                 
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                   
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0130000000]                                          
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                         
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]                         
[    0.000000]   #2 [0000200000 - 0000b854b0]    TEXT DATA BSS ==> [0000200000 - 0000b854b0]                         
[    0.000000]   #3 [003785f000 - 0037fef5e3]          RAMDISK ==> [003785f000 - 0037fef5e3]                         
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                         
[    0.000000]   #5 [0000010000 - 0000014000]          PGTABLE ==> [0000010000 - 0000014000]                         
[    0.000000]   #6 [0000014000 - 0000015000]          PGTABLE ==> [0000014000 - 0000015000]                         
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780                                                     
[    0.000000]  [ffffe20000000000-ffffe200043fffff] PMD -> [ffff880028200000-ffff88002c5fffff] on node 0             
[    0.000000] Zone PFN ranges:                                                                                      
[    0.000000]   DMA      0x00000010 -> 0x00001000                                                                   
[    0.000000]   DMA32    0x00001000 -> 0x00100000                                                                   
[    0.000000]   Normal   0x00100000 -> 0x00130000                                                                   
[    0.000000] Movable zone start PFN for each node                                                                  
[    0.000000] early_node_map[3] active PFN ranges                                                                   
[    0.000000]     0: 0x00000010 -> 0x0000009f                                                                       
[    0.000000]     0: 0x00000100 -> 0x000cffc0                                                                       
[    0.000000]     0: 0x00100000 -> 0x00130000                                                                       
[    0.000000] On node 0 totalpages: 1048399                                                                         
[    0.000000]   DMA zone: 56 pages used for memmap                                                                  
[    0.000000]   DMA zone: 2543 pages reserved                                                                       
[    0.000000]   DMA zone: 1384 pages, LIFO batch:0                                                                  
[    0.000000]   DMA32 zone: 14280 pages used for memmap                                                             
[    0.000000]   DMA32 zone: 833528 pages, LIFO batch:31                                                             
[    0.000000]   Normal zone: 2688 pages used for memmap                                                             
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31                                                            
[    0.000000]   Movable zone: 0 pages used for memmap                                                               
[    0.000000] Detected use of extended apic ids on hypertransport bus                                               
[    0.000000] ACPI: PM-Timer IO Port: 0x808                                                                         
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                   
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)                                                    
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)                                                   
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)                                                   
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])                                               
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23                                         
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                              
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)                                            
[    0.000000] ACPI: IRQ0 used by override.                                                                          
[    0.000000] ACPI: IRQ2 used by override.                                                                          
[    0.000000] ACPI: IRQ9 used by override.                                                                          
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000                                                                
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                   
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs                                                                  
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                                     
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000                                     
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000                                     
[    0.000000] PM: Registered nosave memory: 00000000cffc0000 - 00000000cffce000                                     
[    0.000000] PM: Registered nosave memory: 00000000cffce000 - 00000000cfff0000                                     
[    0.000000] PM: Registered nosave memory: 00000000cfff0000 - 00000000cfffe000                                     
[    0.000000] PM: Registered nosave memory: 00000000cfffe000 - 00000000fff00000                                     
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000                                     
[    0.000000] Allocating PCI resources starting at d0000000 (gap: cfffe000:2ff02000)                                
[    0.000000] PERCPU: Allocating 69632 bytes of per cpu data                                                        
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1                                                             
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1028832                          
[    0.000000] Kernel command line: root=UUID=3a675246-e744-4082-80d9-5fe63a63e862 ro quiet splash                   
[    0.000000] Initializing CPU#0                                                                                    
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)                                                 
[    0.000000] Fast TSC calibration using PIT                                                                        
[    0.000000] Detected 2699.783 MHz processor.                                                                      
[    0.004000] Console: colour VGA+ 80x25                                                                            
[    0.004000] console [tty0] enabled                                                                                
[    0.004000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)                                    
[    0.004000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)                                      
[    0.004000] allocated 49807360 bytes of page_cgroup                                                               
[    0.004000] please try cgroup_disable=memory option if you don't want                                             
[    0.004000] Scanning for low memory corruption every 60 seconds                                                   
[    0.004000] Checking aperture...                                                                                  
[    0.004000] No AGP bridge found                                                                                   
[    0.004000] Node 0: aperture @ dc00000000 size 32 MB                                                              
[    0.004000] Aperture beyond 4GB. Ignoring.                                                                        
[    0.004000] Your BIOS doesn't leave a aperture memory hole                                                        
[    0.004000] Please enable the IOMMU option in the BIOS setup                                                      
[    0.004000] This costs you 64 MB of RAM                                                                           
[    0.004000] Mapping aperture over 65536 KB of RAM @ 20000000                                                      
[    0.004000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000                                     
[    0.004000] Memory: 3984760k/4980736k available (4760k kernel code, 787140k absent, 207960k reserved, 2540k data, 536k init)                                                                                                           
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1                               
[    0.004000] hpet clockevent registered                                                                            
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer                                      
[    0.004008] Calibrating delay loop (skipped), value calculated using timer frequency.. 5399.56 BogoMIPS (lpj=10799132)                                                                                                                 
[    0.004024] Security Framework initialized                                                                        
[    0.004030] SELinux:  Disabled at boot.                                                                           
[    0.004039] AppArmor: AppArmor initialized                                                                        
[    0.004046] Mount-cache hash table entries: 256                                                                   
[    0.004159] Initializing cgroup subsys ns                                                                         
[    0.004161] Initializing cgroup subsys cpuacct                                                                    
[    0.004164] Initializing cgroup subsys memory                                                                     
[    0.004166] Initializing cgroup subsys freezer                                                                    
[    0.004176] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)                                     
[    0.004178] CPU: L2 Cache: 512K (64 bytes/line)                                                                   
[    0.004179] tseg: 0000000000                                                                                      
[    0.004188] CPU: Physical Processor ID: 0                                                                         
[    0.004189] CPU: Processor Core ID: 0                                                                             
[    0.004191] using C1E aware idle routine                                                                          
[    0.005369] ACPI: Core revision 20080926                                                                          
[    0.007344] ACPI: Checking initramfs for custom DSDT                                                              
[    0.235541] Setting APIC routing to flat                                                                          
[    0.236165] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1                                                  
[    0.276083] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02                                      
[    0.280001] Booting processor 1 APIC 0x1 ip 0x6000                                                                
[    0.004000] Initializing CPU#1                                                                                    
[    0.004000] Calibrating delay using timer specific routine.. 5400.39 BogoMIPS (lpj=10800797)                      
[    0.004000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)                                     
[    0.004000] CPU: L2 Cache: 512K (64 bytes/line)                                                                   
[    0.004000] CPU: Physical Processor ID: 0                                                                         
[    0.004000] CPU: Processor Core ID: 1                                                                             
[    0.364170] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ stepping 02                                      
[    0.364181] Brought up 2 CPUs                                                                                     
[    0.364183] Total of 2 processors activated (10799.96 BogoMIPS).                                                  
[    0.364222] CPU0 attaching sched-domain:                                                                          
[    0.364224]  domain 0: span 0-1 level CPU                                                                         
[    0.364226]   groups: 0 1                                                                                         
[    0.364230] CPU1 attaching sched-domain:                                                                          
[    0.364231]  domain 0: span 0-1 level CPU                                                                         
[    0.364232]   groups: 1 0                                                                                         
[    0.364280] net_namespace: 1400 bytes                                                                             
[    0.364280] Booting paravirtualized kernel on bare hardware                                                       
[    0.364280] Time: 20:15:55  Date: 06/07/09                                                                        
[    0.364280] regulator: core version 0.5                                                                           
[    0.364280] NET: Registered protocol family 16                                                                    
[    0.364280] node 0 link 0: io port [1000, ffffff]                                                                 
[    0.364280] TOM: 00000000d0000000 aka 3328M                                                                       
[    0.364280] node 0 link 0: mmio [e0000000, efffffff]                                                              
[    0.364280] node 0 link 0: mmio [f0000000, ffffffff]                                                              
[    0.364280] node 0 link 0: mmio [a0000, bffff]                                                                    
[    0.364280] node 0 link 0: mmio [d0000000, dfffffff]                                                              
[    0.364280] TOM2: 0000000130000000 aka 4864M                                                                      
[    0.364280] bus: [00,07] on node 0 link 0                                                                         
[    0.364280] bus: 00 index 0 io port: [0, ffff]                                                                    
[    0.364280] bus: 00 index 1 mmio: [d0000000, ffffffff]                                                            
[    0.364280] bus: 00 index 2 mmio: [a0000, bffff]                                                                  
[    0.364280] bus: 00 index 3 mmio: [130000000, fcffffffff]                                                         
[    0.364280] ACPI: bus type pci registered                                                                         
[    0.364280] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                      
[    0.364280] PCI: Not using MMCONFIG.                                                                              
[    0.364280] PCI: Using configuration type 1 for base access                                                       
[    0.364679] ACPI: EC: Look up EC in DSDT                                                                          
[    0.373752] ACPI: Interpreter enabled                                                                             
[    0.373755] ACPI: (supports S0 S1 S3 S4 S5)                                                                       
[    0.373776] ACPI: Using IOAPIC for interrupt routing                                                              
[    0.373827] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255                                      
[    0.376631] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources                                     
[    0.387449] PCI: Using MMCONFIG at e0000000 - efffffff                                                            
[    0.393901] ACPI: No dock devices found.                                                                          
[    0.393956] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                
[    0.394005] pci 0000:00:00.0: reg 1c 64bit mmio: [0xe0000000-0xffffffff]                                          
[    0.394044] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold                                                 
[    0.394047] pci 0000:00:02.0: PME# disabled                                                                       
[    0.394077] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold                                                 
[    0.394079] pci 0000:00:05.0: PME# disabled                                                                       
[    0.394109] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold                                                 
[    0.394111] pci 0000:00:09.0: PME# disabled                                                                       
[    0.394158] pci 0000:00:12.0: reg 10 io port: [0xa000-0xa007]                                                     
[    0.394165] pci 0000:00:12.0: reg 14 io port: [0x9000-0x9003]                                                     
[    0.394172] pci 0000:00:12.0: reg 18 io port: [0x8000-0x8007]                                                     
[    0.394179] pci 0000:00:12.0: reg 1c io port: [0x7000-0x7003]                                                     
[    0.394186] pci 0000:00:12.0: reg 20 io port: [0x6000-0x600f]                                                     
[    0.394193] pci 0000:00:12.0: reg 24 32bit mmio: [0xfe8ff800-0xfe8ffbff]                                          
[    0.394212] pci 0000:00:12.0: set SATA to AHCI mode                                                               
[    0.394241] pci 0000:00:13.0: reg 10 32bit mmio: [0xfe8fe000-0xfe8fefff]                                          
[    0.394297] pci 0000:00:13.1: reg 10 32bit mmio: [0xfe8fd000-0xfe8fdfff]                                          
[    0.394352] pci 0000:00:13.2: reg 10 32bit mmio: [0xfe8fc000-0xfe8fcfff]                                          
[    0.394408] pci 0000:00:13.3: reg 10 32bit mmio: [0xfe8fb000-0xfe8fbfff]                                          
[    0.394464] pci 0000:00:13.4: reg 10 32bit mmio: [0xfe8fa000-0xfe8fafff]                                          
[    0.394539] pci 0000:00:13.5: reg 10 32bit mmio: [0xfe8ff000-0xfe8ff0ff]                                          
[    0.394580] pci 0000:00:13.5: supports D1 D2                                                                      
[    0.394581] pci 0000:00:13.5: PME# supported from D0 D1 D2 D3hot                                                  
[    0.394585] pci 0000:00:13.5: PME# disabled                                                                       
[    0.394631] pci 0000:00:14.0: reg 10 io port: [0xb00-0xb0f]                                                       
[    0.394693] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]                                                         
[    0.394700] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]                                                         
[    0.394707] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]                                                         
[    0.394713] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]                                                         
[    0.394720] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]                                                     
[    0.394920] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]                                          
[    0.394928] pci 0000:01:00.0: reg 18 64bit mmio: [0xfe9f0000-0xfe9fffff]                                          
[    0.394933] pci 0000:01:00.0: reg 20 io port: [0xb000-0xb0ff]                                                     
[    0.394942] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe9c0000-0xfe9dffff]                                          
[    0.394949] pci 0000:01:00.0: supports D1 D2                                                                      
[    0.394979] pci 0000:01:00.1: reg 10 64bit mmio: [0xfe9e0000-0xfe9effff]                                          
[    0.395004] pci 0000:01:00.1: supports D1 D2                                                                      
[    0.395058] pci 0000:00:02.0: bridge io port: [0xb000-0xbfff]                                                     
[    0.395061] pci 0000:00:02.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]                                          
[    0.395065] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]                                     
[    0.395111] pci 0000:02:00.0: reg 10 io port: [0xc800-0xc8ff]                                                     
[    0.395129] pci 0000:02:00.0: reg 18 64bit mmio: [0xfeaff000-0xfeafffff]                                          
[    0.395147] pci 0000:02:00.0: reg 30 32bit mmio: [0xfeac0000-0xfeadffff]                                          
[    0.395157] pci 0000:02:00.0: supports D1 D2                                                                      
[    0.395158] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold                                              
[    0.395163] pci 0000:02:00.0: PME# disabled                                                                       
[    0.395218] pci 0000:00:05.0: bridge io port: [0xc000-0xcfff]                                                     
[    0.395221] pci 0000:00:05.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]                                          
[    0.395318] pci 0000:04:00.0: reg 10 32bit mmio: [0xfebff800-0xfebfffff]                                          
[    0.395327] pci 0000:04:00.0: reg 14 io port: [0xe800-0xe87f]                                                     
[    0.395374] pci 0000:04:00.0: supports D2                                                                         
[    0.395376] pci 0000:04:00.0: PME# supported from D2 D3hot D3cold                                                 
[    0.395380] pci 0000:04:00.0: PME# disabled                                                                       
[    0.395429] pci 0000:04:03.0: reg 10 io port: [0xe400-0xe41f]                                                     
[    0.395437] pci 0000:04:03.0: reg 14 io port: [0xe000-0xe00f]                                                     
[    0.395446] pci 0000:04:03.0: reg 18 io port: [0xd800-0xd80f]                                                     
[    0.395454] pci 0000:04:03.0: reg 1c io port: [0xd400-0xd43f]                                                     
[    0.395485] pci 0000:04:03.0: supports D2                                                                         
[    0.395540] pci 0000:00:14.4: transparent bridge                                                                  
[    0.395544] pci 0000:00:14.4: bridge io port: [0xd000-0xefff]                                                     
[    0.395548] pci 0000:00:14.4: bridge 32bit mmio: [0xfeb00000-0xfebfffff]                                          
[    0.395565] bus 00 -> node 0                                                                                      
[    0.395572] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                   
[    0.395900] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]                                              
[    0.395991] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE5._PRT]                                              
[    0.396088] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE9._PRT]                                              
[    0.396188] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]                                              
[    0.398765] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 10 11 12 14 15)                                        
[    0.398869] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 *15)                                        
[    0.398973] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)                                        
[    0.399078] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *10 11 12 14 15)                                        
[    0.399181] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.                           
[    0.399287] ACPI: PCI Interrupt Link [LNKF] (IRQs *9)                                                             
[    0.399389] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 *11 12 14 15)                                        
[    0.399492] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)                                        
[    0.399589] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 01, should be F8 [20080926]         
[    0.399630] ACPI: WMI: Mapper loaded                                                                              
[    0.399693] SCSI subsystem initialized                                                                            
[    0.399693] libata version 3.00 loaded.                                                                           
[    0.399693] usbcore: registered new interface driver usbfs                                                        
[    0.399693] usbcore: registered new interface driver hub                                                          
[    0.399693] usbcore: registered new device driver usb                                                             
[    0.400007] PCI: Using ACPI for IRQ routing                                                                       
[    0.400016] pci 0000:00:00.0: BAR 3: can't allocate resource                                                      
[    0.412007] Bluetooth: Core ver 2.13                                                                              
[    0.412019] NET: Registered protocol family 31                                                                    
[    0.412019] Bluetooth: HCI device and connection manager initialized                                              
[    0.412019] Bluetooth: HCI socket layer initialized                                                               
[    0.412019] NET: Registered protocol family 8                                                                     
[    0.412019] NET: Registered protocol family 20                                                                    
[    0.412025] NetLabel: Initializing                                                                                
[    0.412026] NetLabel:  domain hash size = 128                                                                     
[    0.412027] NetLabel:  protocols = UNLABELED CIPSOv4                                                              
[    0.412038] NetLabel:  unlabeled traffic allowed by default                                                       
[    0.412182] PCI-DMA: Disabling AGP.                                                                               
[    0.412252] PCI-DMA: aperture base @ 20000000 size 65536 KB                                                       
[    0.412253] PCI-DMA: using GART IOMMU.                                                                            
[    0.412256] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture                                             
[    0.412689] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0                                                            
[    0.412695] hpet0: 4 comparators, 32-bit 14.318180 MHz counter                                                    
[    0.416066] AppArmor: AppArmor Filesystem Enabled                                                                 
[    0.420013] Switched to high resolution mode on CPU 0                                                             
[    0.420151] Switched to high resolution mode on CPU 1                                                             
[    0.428015] pnp: PnP ACPI init                                                                                    
[    0.428030] ACPI: bus type pnp registered                                                                         
[    0.430852] pnp 00:0c: mem resource (0x0-0x9ffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling         
[    0.430855] pnp 00:0c: mem resource (0xc0000-0xcffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling     
[    0.430857] pnp 00:0c: mem resource (0xe0000-0xfffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling     
[    0.430859] pnp 00:0c: mem resource (0x100000-0xcfffffff) overlaps 0000:00:00.0 BAR 3 (0x0-0x1fffffff), disabling 
[    0.431145] pnp: PnP ACPI: found 13 devices                                                                       
[    0.431146] ACPI: ACPI bus type pnp unregistered                                                                  
[    0.431155] system 00:08: iomem range 0xfec00000-0xfec00fff has been reserved                                     
[    0.431157] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved                                     
[    0.431162] system 00:09: ioport range 0x4d0-0x4d1 has been reserved                                              
[    0.431164] system 00:09: ioport range 0x40b-0x40b has been reserved                                              
[    0.431166] system 00:09: ioport range 0x4d6-0x4d6 has been reserved                                              
[    0.431168] system 00:09: ioport range 0xc00-0xc01 has been reserved                                              
[    0.431169] system 00:09: ioport range 0xc14-0xc14 has been reserved                                              
[    0.431171] system 00:09: ioport range 0xc50-0xc51 has been reserved                                              
[    0.431173] system 00:09: ioport range 0xc52-0xc52 has been reserved                                              
[    0.431175] system 00:09: ioport range 0xc6c-0xc6c has been reserved                                              
[    0.431176] system 00:09: ioport range 0xc6f-0xc6f has been reserved                                              
[    0.431178] system 00:09: ioport range 0xcd0-0xcd1 has been reserved                                              
[    0.431180] system 00:09: ioport range 0xcd2-0xcd3 has been reserved                                              
[    0.431182] system 00:09: ioport range 0xcd4-0xcd5 has been reserved                                              
[    0.431183] system 00:09: ioport range 0xcd6-0xcd7 has been reserved                                              
[    0.431185] system 00:09: ioport range 0xcd8-0xcdf has been reserved                                              
[    0.431187] system 00:09: ioport range 0x800-0x89f has been reserved                                              
[    0.431189] system 00:09: ioport range 0xb10-0xb1f has been reserved                                              
[    0.431191] system 00:09: ioport range 0x900-0x90f has been reserved                                              
[    0.431192] system 00:09: ioport range 0x910-0x91f has been reserved                                              
[    0.431194] system 00:09: ioport range 0xfe00-0xfefe has been reserved                                            
[    0.431196] system 00:09: iomem range 0xffb80000-0xffbfffff has been reserved                                     
[    0.431200] system 00:0a: ioport range 0x600-0x6df has been reserved                                              
[    0.431202] system 00:0a: ioport range 0xae0-0xaef has been reserved                                              
[    0.431206] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved                                     
[    0.431210] system 00:0c: iomem range 0xfec00000-0xffffffff could not be reserved                                 
[    0.435847] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01                                                   
[    0.435850] pci 0000:00:02.0:   IO window: 0xb000-0xbfff                                                          
[    0.435853] pci 0000:00:02.0:   MEM window: 0xfe900000-0xfe9fffff                                                 
[    0.435856] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff                                
[    0.435859] pci 0000:00:05.0: PCI bridge, secondary bus 0000:02                                                   
[    0.435861] pci 0000:00:05.0:   IO window: 0xc000-0xcfff                                                          
[    0.435864] pci 0000:00:05.0:   MEM window: 0xfea00000-0xfeafffff                                                 
[    0.435866] pci 0000:00:05.0:   PREFETCH window: disabled                                                         
[    0.435869] pci 0000:00:09.0: PCI bridge, secondary bus 0000:03                                                   
[    0.435871] pci 0000:00:09.0:   IO window: disabled                                                               
[    0.435873] pci 0000:00:09.0:   MEM window: disabled                                                              
[    0.435875] pci 0000:00:09.0:   PREFETCH window: disabled                                                         
[    0.435879] pci 0000:00:14.4: PCI bridge, secondary bus 0000:04                                                   
[    0.435881] pci 0000:00:14.4:   IO window: 0xd000-0xefff                                                          
[    0.435886] pci 0000:00:14.4:   MEM window: 0xfeb00000-0xfebfffff                                                 
[    0.435890] pci 0000:00:14.4:   PREFETCH window: disabled                                                         
[    0.435902] pci 0000:00:02.0: setting latency timer to 64                                                         
[    0.435907] pci 0000:00:05.0: setting latency timer to 64                                                         
[    0.435912] pci 0000:00:09.0: setting latency timer to 64                                                         
[    0.435919] bus: 00 index 0 io port: [0x00-0xffff]                                                                
[    0.435920] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]                                                   
[    0.435922] bus: 01 index 0 io port: [0xb000-0xbfff]                                                              
[    0.435923] bus: 01 index 1 mmio: [0xfe900000-0xfe9fffff]                                                         
[    0.435925] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]                                                         
[    0.435926] bus: 01 index 3 mmio: [0x0-0x0]                                                                       
[    0.435927] bus: 02 index 0 io port: [0xc000-0xcfff]                                                              
[    0.435929] bus: 02 index 1 mmio: [0xfea00000-0xfeafffff]                                                         
[    0.435930] bus: 02 index 2 mmio: [0x0-0x0]                                                                       
[    0.435931] bus: 02 index 3 mmio: [0x0-0x0]                                                                       
[    0.435932] bus: 03 index 0 mmio: [0x0-0x0]                                                                       
[    0.435933] bus: 03 index 1 mmio: [0x0-0x0]                                                                       
[    0.435934] bus: 03 index 2 mmio: [0x0-0x0]                                                                       
[    0.435935] bus: 03 index 3 mmio: [0x0-0x0]                                                                       
[    0.435937] bus: 04 index 0 io port: [0xd000-0xefff]                                                              
[    0.435938] bus: 04 index 1 mmio: [0xfeb00000-0xfebfffff]                                                         
[    0.435939] bus: 04 index 2 mmio: [0x0-0x0]                                                                       
[    0.435940] bus: 04 index 3 io port: [0x00-0xffff]                                                                
[    0.435942] bus: 04 index 4 mmio: [0x000000-0xffffffffffffffff]                                                   
[    0.435951] NET: Registered protocol family 2                                                                     
[    0.468054] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)                                   
[    0.468639] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)                                 
[    0.470348] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)                                          
[    0.470804] TCP: Hash tables configured (established 262144 bind 65536)                                           
[    0.470807] TCP reno registered                                                                                   
[    0.480098] NET: Registered protocol family 1                                                                     
[    0.480194] checking if image is initramfs... it is                                                               
[    0.915143] Freeing initrd memory: 7745k freed                                                                    
[    0.919150] audit: initializing netlink socket (disabled)                                                         
[    0.919167] type=2000 audit(1244405754.916:1): initialized                                                        
[    0.925310] HugeTLB registered 2 MB page size, pre-allocated 0 pages                                              
[    0.926166] VFS: Disk quotas dquot_6.5.1                                                                          
[    0.926203] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)                                             
[    0.926638] fuse init (API version 7.10)                                                                          
[    0.926692] msgmni has been set to 7799                                                                           
[    0.926849] alg: No test for stdrng (krng)                                                                        
[    0.926861] io scheduler noop registered                                                                          
[    0.926862] io scheduler anticipatory registered                                                                  
[    0.926863] io scheduler deadline registered                                                                      
[    0.926896] io scheduler cfq registered (default)                                                                 
[    1.032539] pci 0000:01:00.0: Boot video device                                                                   
[    1.035433] pcieport-driver 0000:00:02.0: setting latency timer to 64                                             
[    1.035457] pcieport-driver 0000:00:02.0: found MSI capability                                                    
[    1.035477] pcieport-driver 0000:00:02.0: irq 2303 for MSI/MSI-X                                                  
[    1.035485] pci_express 0000:00:02.0:pcie00: allocate port service                                                
[    1.035495] pci_express 0000:00:02.0:pcie03: allocate port service                                                
[    1.035530] pcieport-driver 0000:00:05.0: setting latency timer to 64                                             
[    1.035553] pcieport-driver 0000:00:05.0: found MSI capability                                                    
[    1.035569] pcieport-driver 0000:00:05.0: irq 2302 for MSI/MSI-X                                                  
[    1.035576] pci_express 0000:00:05.0:pcie00: allocate port service                                                
[    1.035587] pci_express 0000:00:05.0:pcie03: allocate port service                                                
[    1.035622] pcieport-driver 0000:00:09.0: setting latency timer to 64                                             
[    1.035645] pcieport-driver 0000:00:09.0: found MSI capability                                                    
[    1.035661] pcieport-driver 0000:00:09.0: irq 2301 for MSI/MSI-X                                                  
[    1.035668] pci_express 0000:00:09.0:pcie00: allocate port service                                                
[    1.035676] pci_express 0000:00:09.0:pcie03: allocate port service                                                
[    1.035719] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                       
[    1.035725] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                           
[    1.035823] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                             
[    1.035825] ACPI: Power Button (FF) [PWRF]                                                                        
[    1.035862] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                    
[    1.035869] ACPI: Power Button (CM) [PWRB]                                                                        
[    1.036099] ACPI: duty_cycle spans bit 4                                                                          
[    1.036123] processor ACPI_CPU:00: registered as cooling_device0                                                  
[    1.036149] processor ACPI_CPU:01: registered as cooling_device1                                                  
[    1.064688] Linux agpgart interface v0.103                                                                        
[    1.064696] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                 
[    1.064805] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                  
[    1.065039] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                       
[    1.065596] brd: module loaded                                                                                    
[    1.065815] loop: module loaded                                                                                   
[    1.065867] Fixed MDIO Bus: probed                                                                                
[    1.065871] PPP generic driver version 2.4.2                                                                      
[    1.065913] input: Macintosh mouse button emulation as /devices/virtual/input/input2                              
[    1.065938] Driver 'sd' needs updating - please use bus_type methods                                              
[    1.065944] Driver 'sr' needs updating - please use bus_type methods                                              
[    1.065972] ahci 0000:00:12.0: version 3.0                                                                        
[    1.065990] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22                                         
[    1.066023] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit                                       
[    1.066105] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode                          
[    1.066108] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part                                  
[    1.066577] scsi0 : ahci                                                                                          
[    1.066694] scsi1 : ahci                                                                                          
[    1.066749] scsi2 : ahci                                                                                          
[    1.066806] scsi3 : ahci                                                                                          
[    1.066873] ata1: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22                         
[    1.066876] ata2: SATA max UDMA/133 irq_stat 0x00400040, connection status changed irq 22                         
[    1.066879] ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 22                                  
[    1.066882] ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 22                                  
[    1.952023] ata1: softreset failed (device not ready)                                                             
[    1.952069] ata1: failed due to HW bug, retry pmp=0                                                               
[    2.116029] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                                                
[    2.116900] ata1.00: ATA-7: Hitachi HDT725025VLA380, V5DOA52A, max UDMA/133                                       
[    2.116902] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)                                         
[    2.116915] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    2.117971] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    2.117973] ata1.00: configured for UDMA/133                                                                      
[    3.020016] ata2: softreset failed (device not ready)                                                             
[    3.020062] ata2: failed due to HW bug, retry pmp=0                                                               
[    3.184027] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)                                                
[    3.196912] ata2.00: ATA-7: Hitachi HDT725025VLA380, V5DOA52A, max UDMA/133                                       
[    3.196914] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)                                         
[    3.196928] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    3.197799] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    3.197801] ata2.00: configured for UDMA/133                                                                      
[    3.696016] ata3: softreset failed (device not ready)                                                             
[    3.696060] ata3: failed due to HW bug, retry pmp=0                                                               
[    3.860026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)                                                
[    3.860226] ata3.00: ATAPI: ATAPI   iHAS120   6, 7L0E, max UDMA/100                                               
[    3.860240] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    3.860896] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    3.860897] ata3.00: configured for UDMA/100                                                                      
[    4.360017] ata4: softreset failed (device not ready)                                                             
[    4.360060] ata4: failed due to HW bug, retry pmp=0                                                               
[    4.524026] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)                                                
[    4.524229] ata4.00: ATAPI: ATAPI   iHAS120   6, 7L0E, max UDMA/100                                               
[    4.524243] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    4.524917] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd                                                  
[    4.524918] ata4.00: configured for UDMA/100                                                                      
[    4.540105] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5                          
[    4.540172] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)                               
[    4.540188] sd 0:0:0:0: [sda] Write Protect is off                                                                
[    4.540189] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                             
[    4.540207] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA               
[    4.540264] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)                               
[    4.540274] sd 0:0:0:0: [sda] Write Protect is off                                                                
[    4.540276] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                             
[    4.540292] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA               
[    4.540295]  sda: sda1 sda2 < sda5 >                                                                              
[    4.572157] sd 0:0:0:0: [sda] Attached SCSI disk                                                                  
[    4.572197] sd 0:0:0:0: Attached scsi generic sg0 type 0                                                          
[    4.572245] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5                          
[    4.572308] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)                               
[    4.572318] sd 1:0:0:0: [sdb] Write Protect is off                                                                
[    4.572320] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00                                                             
[    4.572337] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA               
[    4.572371] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)                               
[    4.572380] sd 1:0:0:0: [sdb] Write Protect is off                                                                
[    4.572382] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00                                                             
[    4.572399] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA               
[    4.572402]  sdb: sdb1                                                                                            
[    4.587801] sd 1:0:0:0: [sdb] Attached SCSI disk                                                                  
[    4.587826] sd 1:0:0:0: Attached scsi generic sg1 type 0                                                          
[    4.588802] scsi 2:0:0:0: CD-ROM            ATAPI    iHAS120   6      7L0E PQ: 0 ANSI: 5                          
[    4.594294] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray                                 
[    4.594297] Uniform CD-ROM driver Revision: 3.20                                                                  
[    4.594365] sr 2:0:0:0: Attached scsi CD-ROM sr0                                                                  
[    4.594391] sr 2:0:0:0: Attached scsi generic sg2 type 5                                                          
[    4.595364] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS120   6      7L0E PQ: 0 ANSI: 5                          
[    4.600863] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray                                 
[    4.600904] sr 3:0:0:0: Attached scsi CD-ROM sr1                                                                  
[    4.600928] sr 3:0:0:0: Attached scsi generic sg3 type 5                                                          
[    4.601116] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                  
[    4.601149] pata_atiixp 0000:00:14.1: setting latency timer to 64                                                 
[    4.601244] scsi4 : pata_atiixp                                                                                   
[    4.601316] scsi5 : pata_atiixp                                                                                   
[    4.602334] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14                                       
[    4.602336] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15                                       
[    4.912336] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                            
[    4.912353] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19                                     
[    4.912369] ehci_hcd 0000:00:13.5: EHCI Host Controller                                                           
[    4.912411] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1                                  
[    4.912436] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround                                 
[    4.912455] ehci_hcd 0000:00:13.5: debug port 1                                                                   
[    4.912471] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe8ff000                                                      
[    4.924018] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00                                                     
[    4.924082] usb usb1: configuration #1 chosen from 1 choice                                                       
[    4.924102] hub 1-0:1.0: USB hub found                                                                            
[    4.924108] hub 1-0:1.0: 10 ports detected                                                                        
[    4.924201] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                
[    4.924212] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16                                     
[    4.924221] ohci_hcd 0000:00:13.0: OHCI Host Controller                                                           
[    4.924250] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2                                  
[    4.924268] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe8fe000                                                      
[    4.984034] usb usb2: configuration #1 chosen from 1 choice                                                       
[    4.984051] hub 2-0:1.0: USB hub found                                                                            
[    4.984061] hub 2-0:1.0: 2 ports detected                                                                         
[    4.984122] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                     
[    4.984130] ohci_hcd 0000:00:13.1: OHCI Host Controller                                                           
[    4.984156] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3                                  
[    4.984175] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe8fd000                                                      
[    5.040035] usb usb3: configuration #1 chosen from 1 choice                                                       
[    5.040055] hub 3-0:1.0: USB hub found                                                                            
[    5.040063] hub 3-0:1.0: 2 ports detected                                                                         
[    5.040123] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                     
[    5.040132] ohci_hcd 0000:00:13.2: OHCI Host Controller                                                           
[    5.040159] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4                                  
[    5.040178] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe8fc000                                                      
[    5.096036] usb usb4: configuration #1 chosen from 1 choice                                                       
[    5.096051] hub 4-0:1.0: USB hub found                                                                            
[    5.096059] hub 4-0:1.0: 2 ports detected                                                                         
[    5.096119] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17                                     
[    5.096128] ohci_hcd 0000:00:13.3: OHCI Host Controller                                                           
[    5.096165] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5                                  
[    5.096177] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe8fb000                                                      
[    5.152036] usb usb5: configuration #1 chosen from 1 choice                                                       
[    5.152053] hub 5-0:1.0: USB hub found                                                                            
[    5.152061] hub 5-0:1.0: 2 ports detected                                                                         
[    5.152120] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18                                     
[    5.152129] ohci_hcd 0000:00:13.4: OHCI Host Controller                                                           
[    5.152156] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6                                  
[    5.152168] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe8fa000                                                      
[    5.208037] usb usb6: configuration #1 chosen from 1 choice                                                       
[    5.208055] hub 6-0:1.0: USB hub found                                                                            
[    5.208063] hub 6-0:1.0: 2 ports detected                                                                         
[    5.208130] uhci_hcd: USB Universal Host Controller Interface driver                                              
[    5.208188] usbcore: registered new interface driver libusual                                                     
[    5.208212] usbcore: registered new interface driver usbserial                                                    
[    5.208219] USB Serial support registered for generic                                                             
[    5.348015] usb 1-6: new high speed USB device using ehci_hcd and address 4                                       
[    5.482223] usb 1-6: configuration #1 chosen from 1 choice                                                        
[    5.592015] usb 1-9: new high speed USB device using ehci_hcd and address 5                                       
[    5.724380] usb 1-9: configuration #1 chosen from 1 choice                                                        
[    5.724491] hub 1-9:1.0: USB hub found                                                                            
[    5.724603] hub 1-9:1.0: 4 ports detected                                                                         
[    5.725516] usbcore: registered new interface driver usbserial_generic                                            
[    5.725518] usbserial: USB Serial Driver core                                                                     
[    5.725548] PNP: No PS/2 controller found. Probing ports directly.                                                
[    5.727479] serio: i8042 KBD port at 0x60,0x64 irq 1                                                              
[    5.727483] serio: i8042 AUX port at 0x60,0x64 irq 12                                                             
[    5.736539] mice: PS/2 mouse device common for all mice                                                           
[    5.772554] rtc_cmos 00:02: RTC can wake from S4                                                                  
[    5.772583] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0                                                 
[    5.772608] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs                                         
[    5.772663] device-mapper: uevent: version 1.0.3                                                                  
[    5.772766] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com                      
[    5.772917] device-mapper: multipath: version 1.0.5 loaded                                                        
[    5.772919] device-mapper: multipath round-robin: version 1.0.0 loaded                                            
[    5.773095] cpuidle: using governor ladder                                                                        
[    5.773096] cpuidle: using governor menu                                                                          
[    5.773407] TCP cubic registered                                                                                  
[    5.773458] NET: Registered protocol family 10                                                                    
[    5.773751] lo: Disabled Privacy Extensions                                                                       
[    5.773948] NET: Registered protocol family 17                                                                    
[    5.773965] Bluetooth: L2CAP ver 2.11                                                                             
[    5.773966] Bluetooth: L2CAP socket layer initialized                                                             
[    5.773968] Bluetooth: SCO (Voice Link) ver 0.6                                                                   
[    5.773969] Bluetooth: SCO socket layer initialized                                                               
[    5.774010] Bluetooth: RFCOMM socket layer initialized                                                            
[    5.774016] Bluetooth: RFCOMM TTY layer initialized                                                               
[    5.774017] Bluetooth: RFCOMM ver 1.10                                                                            
[    5.774055] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (2 cpu cores) (version 2.20.00)                                                                                                             
[    5.774073] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.                              
[    5.774138] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.                              
[    5.774260] registered taskstats version 1                                                                        
[    5.774378]   Magic number: 13:366:295                                                                            
[    5.774404] tty tty28: hash matches                                                                               
[    5.774459] rtc_cmos 00:02: setting system clock to 2009-06-07 20:16:00 UTC (1244405760)                          
[    5.774462] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                  
[    5.774463] EDD information not available.                                                                        
[    5.774490] Freeing unused kernel memory: 536k freed                                                              
[    5.774716] Write protecting the kernel read-only data: 6708k                                                     
[    5.860520] usb 3-1: new low speed USB device using ohci_hcd and address 2                                        
[    5.926074] Floppy drive(s): fd0 is 1.44M                                                                         
[    5.946978] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded                                                       
[    5.946998] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                        
[    5.947015] r8169 0000:02:00.0: setting latency timer to 64                                                       
[    5.947119] r8169 0000:02:00.0: irq 2300 for MSI/MSI-X                                                            
[    5.947561] eth0: RTL8168b/8111b at 0xffffc2001009c000, 00:21:85:14:b5:eb, XID 38000000 IRQ 2300                  
[    5.949847] FDC 0 is a post-1991 82077                                                                            
[    6.033944] ohci1394 0000:04:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23                                     
[    6.085701] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[febff800-febfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]                                                                                                       
[    6.112141] usb 3-1: configuration #1 chosen from 1 choice                                                        
[    6.291142] usbcore: registered new interface driver hiddev                                                       
[    6.302313] input:   USB Keyboard as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input3               
[    6.324559] generic-usb 0003:1241:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:13.1-1/input0                                                                                                       
[    6.347101] input:   USB Keyboard as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.1/input/input4               
[    6.368553] generic-usb 0003:1241:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:13.1-1/input1                                                                                                         
[    6.368568] usbcore: registered new interface driver usbhid                                                       
[    6.368571] usbhid: v2.6:USB HID core driver                                                                      
[    6.376524] usb 3-2: new low speed USB device using ohci_hcd and address 3                                        
[    6.469523] PM: Starting manual resume from disk                                                                  
[    6.469526] PM: Resume from partition 8:5                                                                         
[    6.469527] PM: Checking hibernation image.                                                                       
[    6.469667] PM: Resume from disk failed.                                                                          
[    6.509477] kjournald starting.  Commit interval 5 seconds                                                        
[    6.509486] EXT3-fs: mounted filesystem with ordered data mode.                                                   
[    6.546113] usb 3-2: configuration #1 chosen from 1 choice                                                        
[    6.554301] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input5                                                                                                                   
[    6.584549] generic-usb 0003:046D:C040.0003: input,hidraw2: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.1-2/input0                                                                                         
[    6.656612] usb 1-9.4: new high speed USB device using ehci_hcd and address 6                                     
[    6.750186] usb 1-9.4: configuration #1 chosen from 1 choice                                                      
[    7.236019] Initializing USB Mass Storage driver...                                                               
[    7.236254] scsi6 : SCSI emulation for USB Mass Storage devices                                                   
[    7.236356] usb-storage: device found at 4                                                                        
[    7.236357] usb-storage: waiting for device to settle before scanning                                             
[    7.236422] scsi7 : SCSI emulation for USB Mass Storage devices                                                   
[    7.236493] usbcore: registered new interface driver usb-storage                                                  
[    7.236495] USB Mass Storage support registered.                                                                  
[    7.236617] usb-storage: device found at 6                                                                        
[    7.236618] usb-storage: waiting for device to settle before scanning                                             
[    7.368096] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00dc100001642ce6]                                       
[   11.235848] udev: starting version 141                                                                            
[   11.574532] input: PC Speaker as /devices/platform/pcspkr/input/input6                                            
[   11.753795] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]            
[   11.753798] ACPI: Device needs an ACPI driver                                                                     
[   11.753806] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0                                  
[   12.070242] ICE1712 0000:04:03.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21                                      
[   12.237777] usb-storage: device scan complete                                                                     
[   12.238821] usb-storage: device scan complete                                                                     
[   12.239003] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2                          
[   12.240381] scsi 7:0:0:1: CD-ROM            SanDisk  U3 Cruzer Micro  4.05 PQ: 0 ANSI: 2                          
[   12.242382] scsi 6:0:0:0: Direct-Access     IC25N060 ATMR04-0         0000 PQ: 0 ANSI: 0                          
[   12.242490] sd 7:0:0:0: [sdc] 8013453 512-byte hardware sectors: (4.10 GB/3.82 GiB)                               
[   12.242975] sd 7:0:0:0: [sdc] Write Protect is off                                                                
[   12.242977] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00                                                             
[   12.242979] sd 7:0:0:0: [sdc] Assuming drive cache: write through                                                 
[   12.244477] sd 7:0:0:0: [sdc] 8013453 512-byte hardware sectors: (4.10 GB/3.82 GiB)                               
[   12.244976] sd 7:0:0:0: [sdc] Write Protect is off                                                                
[   12.244977] sd 7:0:0:0: [sdc] Mode Sense: 03 00 00 00                                                             
[   12.244979] sd 7:0:0:0: [sdc] Assuming drive cache: write through                                                 
[   12.244982]  sdc: sdc1                                                                                            
[   12.245703] sd 7:0:0:0: [sdc] Attached SCSI removable disk                                                        
[   12.245758] sd 7:0:0:0: Attached scsi generic sg4 type 0                                                          
[   12.246479] sr2: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray                                                
[   12.246532] sr 7:0:0:1: Attached scsi CD-ROM sr2                                                                  
[   12.246566] sr 7:0:0:1: Attached scsi generic sg5 type 5                                                          
[   12.247746] sd 6:0:0:0: [sdd] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)                             
[   12.249701] sd 6:0:0:0: [sdd] Write Protect is off                                                                
[   12.249705] sd 6:0:0:0: [sdd] Mode Sense: 27 00 00 00                                                             
[   12.249707] sd 6:0:0:0: [sdd] Assuming drive cache: write through                                                 
[   12.251315] sd 6:0:0:0: [sdd] 117210240 512-byte hardware sectors: (60.0 GB/55.8 GiB)                             
[   12.252257] sd 6:0:0:0: [sdd] Write Protect is off                                                                
[   12.252261] sd 6:0:0:0: [sdd] Mode Sense: 27 00 00 00                                                             
[   12.252263] sd 6:0:0:0: [sdd] Assuming drive cache: write through                                                 
[   12.252268]  sdd:<6>lp: driver loaded but no devices found                                                        
[   12.383235] Adding 9936160k swap on /dev/sda5.  Priority:-1 extents:1 across:9936160k                             
[   12.598046]  sdd1                                                                                                 
[   12.598160] sd 6:0:0:0: [sdd] Attached SCSI disk                                                                  
[   12.598218] sd 6:0:0:0: Attached scsi generic sg6 type 0                                                          
[   12.919794] EXT3 FS on sda1, internal journal                                                                     
[   13.870217] type=1505 audit(1244427368.594:2): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2190                                                                                                          
[   13.870330] type=1505 audit(1244427368.594:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2190                                                                                                                
[   13.870367] type=1505 audit(1244427368.594:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2190                                                                                  
[   13.870401] type=1505 audit(1244427368.594:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2190                                                                                       
[   13.972038] type=1505 audit(1244427368.694:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2195                                                                                                 
[   13.972186] type=1505 audit(1244427368.694:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2195                                                                                                                
[   13.996343] type=1505 audit(1244427368.718:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2199                                                                                                              
[   15.950404] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                                                          
[   15.950406] Bluetooth: BNEP filters: protocol multicast                                                           
[   15.958819] Bridge firewalling registered
[   17.177385] ppdev: user-space parallel port driver
[   18.137828] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.292558] [drm] Initialized drm 1.1.0 20060810
[   18.377007] pci 0000:01:00.0: setting latency timer to 64
[   18.377132] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   18.880336] [drm] Setting GART location based on new memory map
[   18.880578] [drm] Loading R500 Microcode
[   18.880604] [drm] Num pipes: 1
[   18.880611] [drm] writeback test succeeded in 1 usecs
[   21.275992] r8169: eth0: link up
[   21.276001] r8169: eth0: link up
[   31.456011] eth0: no IPv6 routers present
[   32.699834] CPU0 attaching NULL sched-domain.
[   32.699839] CPU1 attaching NULL sched-domain.
[   32.712057] CPU0 attaching sched-domain:
[   32.712060]  domain 0: span 0-1 level CPU
[   32.712061]   groups: 0 1
[   32.712065] CPU1 attaching sched-domain:
[   32.712066]  domain 0: span 0-1 level CPU
[   32.712067]   groups: 1 0
[   40.864977] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   40.864981] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   41.081402] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   41.081405] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   41.090144] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   41.090148] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   41.090238] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   41.090240] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   41.433620] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   41.433624] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   41.470113] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   41.470117] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   41.470858] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   41.470861] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   42.783950] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   42.783955] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   46.112360] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   46.112364] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   46.117737] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   46.117740] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   46.131025] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   46.131029] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   47.693416] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   47.693420] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   47.699336] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   47.699340] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   47.706382] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   47.706386] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
[   47.708526] ecryptfs_parse_tag_70_packet: max_packet_size is [56]; real packet size is [51]
[   47.708530] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
drzin@dr_zin:

```

---

### Post by Dr Zin on 2009-11-16
Could someone tell me what hardware is not working. is HDD or My south bridge?


```
vel@redhat.com                                                                 
[    2.046652] device-mapper: multipath: version 1.1.0 loaded                   
[    2.046657] device-mapper: multipath round-robin: version 1.0.0 loaded       
[    2.046825] cpuidle: using governor ladder                                   
[    2.046827] cpuidle: using governor menu                                     
[    2.047167] TCP cubic registered                                             
[    2.047270] NET: Registered protocol family 10                               
[    2.047628] lo: Disabled Privacy Extensions                                  
[    2.047845] NET: Registered protocol family 17                               
[    2.047863] Bluetooth: L2CAP ver 2.13                                        
[    2.047865] Bluetooth: L2CAP socket layer initialized                        
[    2.047867] Bluetooth: SCO (Voice Link) ver 0.6                              
[    2.047869] Bluetooth: SCO socket layer initialized                          
[    2.047900] Bluetooth: RFCOMM TTY layer initialized                          
[    2.047902] Bluetooth: RFCOMM socket layer initialized                       
[    2.047903] Bluetooth: RFCOMM ver 1.11                                       
[    2.047929] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5200+ processors (2 cpu cores) (version 2.20.00)                                   
[    2.047940] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.                                                                              
[    2.047941] [Firmware Bug]: powernow-k8: Try again with latest BIOS.         
[    2.048010] PM: Resume from disk failed.                                     
[    2.048020] registered taskstats version 1                                   
[    2.048149]   Magic number: 1:904:272                                        
[    2.048229] rtc_cmos 00:02: setting system clock to 2009-11-16 09:16:34 UTC (1258362994)                                                                     
[    2.048231] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found             
[    2.048233] EDD information not available.                                   
[    2.121266] usb 1-5: new high speed USB device using ehci_hcd and address 3  
[    2.251265] ata3: softreset failed (device not ready)                        
[    2.251268] ata3: applying SB600 PMP SRST workaround and retrying            
[    2.251284] ata4: softreset failed (device not ready)                        
[    2.251286] ata4: applying SB600 PMP SRST workaround and retrying            
[    2.271690] usb 1-5: configuration #1 chosen from 1 choice                   
[    2.271789] hub 1-5:1.0: USB hub found                                       
[    2.271892] hub 1-5:1.0: 4 ports detected                                    
[    2.430028] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)           
[    2.430054] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)           
[    2.430237] ata4.00: ATAPI: ATAPI   iHAS120   6, 7L0E, max UDMA/100          
[    2.430258] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.430271] ata3.00: ATAPI: ATAPI   iHAS120   6, 7L0E, max UDMA/100          
[    2.430286] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.430930] ata4.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.430932] ata4.00: configured for UDMA/100                                 
[    2.430956] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.430958] ata3.00: configured for UDMA/100                                 
[    2.451266] usb 1-10: new high speed USB device using ehci_hcd and address 5 
[    2.603477] usb 1-10: configuration #1 chosen from 1 choice                  
[    2.650018] ata1: softreset failed (device not ready)                        
[    2.650021] ata1: applying SB600 PMP SRST workaround and retrying            
[    2.650037] ata2: softreset failed (device not ready)                        
[    2.650040] ata2: applying SB600 PMP SRST workaround and retrying            
[    2.740015] usb 3-1: new low speed USB device using ohci_hcd and address 2   
[    2.831273] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)           
[    2.831293] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)           
[    2.841631] ata2.00: ATA-7: Hitachi HDT725025VLA380, V5DOA52A, max UDMA/133  
[    2.841634] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)    
[    2.841650] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.842520] ata2.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.842522] ata2.00: configured for UDMA/133                                 
[    2.842752] ata1.00: ATA-7: Hitachi HDT725025VLA380, V5DOA52A, max UDMA/133  
[    2.842754] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)    
[    2.842770] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.843640] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd             
[    2.843642] ata1.00: configured for UDMA/133                                 
[    2.860109] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5                                                                     
[    2.860209] sd 0:0:0:0: Attached scsi generic sg0 type 0                     
[    2.860241] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)                                                                            
[    2.860276] sd 0:0:0:0: [sda] Write Protect is off                           
[    2.860278] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00                        
[    2.860296] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[    2.860400]  sda:                                                            
[    2.860470] scsi 1:0:0:0: Direct-Access     ATA      Hitachi HDT72502 V5DO PQ: 0 ANSI: 5                                                                     
[    2.860555] sd 1:0:0:0: Attached scsi generic sg1 type 0                     
[    2.860580] sd 1:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)                                                                            
[    2.860613] sd 1:0:0:0: [sdb] Write Protect is off                           
[    2.860615] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00                        
[    2.860631] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[    2.860718]  sdb:                                                            
[    2.861713] scsi 2:0:0:0: CD-ROM            ATAPI    iHAS120   6      7L0E PQ: 0 ANSI: 5                                                                     
[    2.866289] sr0: scsi3-mmc drive: 62x/125x writer dvd-ram cd/rw xa/form2 cdda tray                                                                           
[    2.866291] Uniform CD-ROM driver Revision: 3.20                             
[    2.866360] sr 2:0:0:0: Attached scsi CD-ROM sr0                             
[    2.866391] sr 2:0:0:0: Attached scsi generic sg2 type 5                     
[    2.867366] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS120   6      7L0E PQ: 0 ANSI: 5                                                                     
[    2.872963] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray                                                                            
[    2.873021] sr 3:0:0:0: Attached scsi CD-ROM sr1                             
[    2.873053] sr 3:0:0:0: Attached scsi generic sg3 type 5                     
[    2.874300]  sdb1                                                            
[    2.874450] sd 1:0:0:0: [sdb] Attached SCSI disk                             
[    2.875419]  sda1 sda2 < sda5 >                                              
[    2.898073] sd 0:0:0:0: [sda] Attached SCSI disk                             
[    2.919088] usb 3-1: configuration #1 chosen from 1 choice                   
[    3.030100] Freeing unused kernel memory: 660k freed                         
[    3.030386] Write protecting the kernel read-only data: 7580k                
[    3.148241] [drm] Initialized drm 1.1.0 20060810                             
[    3.213090] [drm] radeon default to kernel modesetting DISABLED.             
[    3.213325] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18     
[    3.213330] pci 0000:01:00.0: setting latency timer to 64                    
[    3.213480] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0                                                                             
[    3.215346] Floppy drive(s): fd0 is 1.44M                                    
[    3.228150]   alloc irq_desc for 23 on node 0                                
[    3.228153]   alloc kstat_irqs on node 0                                     
[    3.228160] ohci1394 0000:03:00.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    3.230407] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded                  
[    3.230427] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17   
[    3.230467] r8169 0000:02:00.0: setting latency timer to 64                  
[    3.230516]   alloc irq_desc for 26 on node 0                                
[    3.230518]   alloc kstat_irqs on node 0                                     
[    3.230530] r8169 0000:02:00.0: irq 26 for MSI/MSI-X                         
[    3.231057] eth0: RTL8168b/8111b at 0xffffc9000065c000, 00:21:85:14:b5:eb, XID 38000000 IRQ 26                                                           
```

---

