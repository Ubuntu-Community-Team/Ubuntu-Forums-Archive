---
title: "Hard crash when deleting large/multiple files?"
date: 2009-09-19
forum: Desktop Environments
---

### Post by w00ly on 2009-09-19
Hello. I'm using Kubuntu on 9.04 and all of a sudden my computer has started having an issue where it will just lock up when I try to delete directories with large or a lot of files. This happens if I do it in dolphin or over my network via ssh and sshfs. When it happens I cant move the mouse, cant push ctrl alt f1, nor alt sysreq k & i, or ctrl alt bkspace. The only thing that works is alt sysreq b for reboot. I'm not really sure what's going on here or why this is doing this so here are my log files...hopefully someone can let me know how to stop this from happening! Thanks in advance!

The messages file is quite large so I wont post the whole thing but I have a lot of these in there, could this be it?
> **messages]Sep 19 19:58:02 htpc kernel: [50100.233461] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled said:**
>  Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
Sep 19 19:58:09 htpc kernel: [50106.362476] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
Sep 19 19:58:09 htpc kernel: [50106.362630] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO


> **dmesg]
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00                                                                   
[    0.000000] Initializing cgroup subsys cpuset                                                                        
[    0.000000] Initializing cgroup subsys cpu                                                                           
[    0.000000] Linux version 2.6.28-15-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 (Ubuntu 2.6.28-15.49-generic)                                                           
[    0.000000] KERNEL supported cpus:                                                                                   
[    0.000000]   Intel GenuineIntel                                                                                     
[    0.000000]   AMD AuthenticAMD                                                                                       
[    0.000000]   NSC Geode by NSC                                                                                       
[    0.000000]   Cyrix CyrixInstead                                                                                     
[    0.000000]   Centaur CentaurHauls                                                                                   
[    0.000000]   Transmeta GenuineTMx86                                                                                 
[    0.000000]   Transmeta TransmetaCPU                                                                                 
[    0.000000]   UMC UMC UMC UMC                                                                                        
[    0.000000] BIOS-provided physical RAM map:                                                                          
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)                                                 
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)                                               
[    0.000000]  BIOS-e820: 00000000000e7000 - 0000000000100000 (reserved)                                               
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003ffc0000 (usable)                                                 
[    0.000000]  BIOS-e820: 000000003ffc0000 - 000000003ffd0000 (ACPI data)                                              
[    0.000000]  BIOS-e820: 000000003ffd0000 - 0000000040000000 (ACPI NVS)                                               
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)                                               
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)                                               
[    0.000000]  BIOS-e820: 00000000ff7c0000 - 0000000100000000 (reserved)                                               
[    0.000000] DMI 2.3 present.                                                                                         
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.                                          
[    0.000000] last_pfn = 0x3ffc0 max_arch_pfn = 0x100000                                                               
[    0.000000] Scanning 0 areas for low memory corruption                                                               
[    0.000000] modified physical RAM map:                                                                               
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)                                                
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)                                                  
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)                                                
[    0.000000]  modified: 00000000000e7000 - 0000000000100000 (reserved)                                                
[    0.000000]  modified: 0000000000100000 - 000000003ffc0000 (usable)                                                  
[    0.000000]  modified: 000000003ffc0000 - 000000003ffd0000 (ACPI data)                                               
[    0.000000]  modified: 000000003ffd0000 - 0000000040000000 (ACPI NVS)                                                
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)                                                
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)                                                
[    0.000000]  modified: 00000000ff7c0000 - 0000000100000000 (reserved)                                                
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000                                                
[    0.000000] RAMDISK: 378c0000 - 37fef6b2                                                                             
[    0.000000] Allocated new RAMDISK: 0087d000 - 00fac6b2                                                               
[    0.000000] Move RAMDISK from 00000000378c0000 - 0000000037fef6b1 to 0087d000 - 00fac6b1                             
[    0.000000] ACPI: RSDP 000FA6D0, 0014 (r0 ACPIAM)                                                                    
[    0.000000] ACPI: RSDT 3FFC0000, 0030 (r1 A M I  OEMRSDT   8000431 MSFT       97)                                    
[    0.000000] ACPI: FACP 3FFC0200, 0081 (r2 A M I  OEMFACP   8000431 MSFT       97)                                    
[    0.000000] ACPI: DSDT 3FFC0400, 356C (r1  N8XLA N8XLA308      308 INTL  2002026)                                    
[    0.000000] ACPI: FACS 3FFD0000, 0040                                                                                
[    0.000000] ACPI: APIC 3FFC0390, 0068 (r1 A M I  OEMAPIC   8000431 MSFT       97)                                    
[    0.000000] ACPI: OEMB 3FFD0040, 0041 (r1 A M I  OEMBIOS   8000431 MSFT       97)                                    
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                      
[    0.000000] 139MB HIGHMEM available.                                                                                 
[    0.000000] 883MB LOWMEM available.                                                                                  
[    0.000000]   mapped low ram: 0 - 373fe000                                                                           
[    0.000000]   low ram: 00000000 - 373fe000                                                                           
[    0.000000]   bootmap 00012000 - 00018e80                                                                            
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]                                             
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                            
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                            
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                            
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]                            
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]                            
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]                            
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]                            
[    0.000000]   #7 [000087d000 - 0000fac6b2]      NEW RAMDISK ==> [000087d000 - 0000fac6b2]                            
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]                            
[    0.000000] found SMP MP-table at [c00ff780] 000ff780                                                                
[    0.000000] Zone PFN ranges:                                                                                         
[    0.000000]   DMA      0x00000010 -> 0x00001000                                                                      
[    0.000000]   Normal   0x00001000 -> 0x000373fe                                                                      
[    0.000000]   HighMem  0x000373fe -> 0x0003ffc0                                                                      
[    0.000000] Movable zone start PFN for each node                                                                     
[    0.000000] early_node_map[2] active PFN ranges                                                                      
[    0.000000]     0: 0x00000010 -> 0x0000009f                                                                          
[    0.000000]     0: 0x00000100 -> 0x0003ffc0                                                                          
[    0.000000] On node 0 totalpages: 261967                                                                             
[    0.000000] free_area_init_node: node 0, pgdat c06cb500, node_mem_map c1000200                                       
[    0.000000]   DMA zone: 32 pages used for memmap                                                                     
[    0.000000]   DMA zone: 0 pages reserved                                                                             
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0                                                                     
[    0.000000]   Normal zone: 1736 pages used for memmap                                                                
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31                                                               
[    0.000000]   HighMem zone: 280 pages used for memmap                                                                
[    0.000000]   HighMem zone: 35498 pages, LIFO batch:7                                                                
[    0.000000]   Movable zone: 0 pages used for memmap                                                                  
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.                                                     
[    0.000000] If you got timer trouble try acpi_use_timer_override                                                     
[    0.000000] ACPI: PM-Timer IO Port: 0x4008                                                                           
[    0.000000] ACPI: Local APIC address 0xfee00000                                                                      
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)                                                       
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])                                                  
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23                                           
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)                                                 
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.                                                                   
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)                                              
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)                                             
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)                                             
[    0.000000] ACPI: IRQ9 used by override.                                                                             
[    0.000000] ACPI: IRQ14 used by override.                                                                            
[    0.000000] ACPI: IRQ15 used by override.                                                                            
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                                                            
[    0.000000] Using ACPI (MADT) for SMP configuration information                                                      
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs                                                                     
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000                                        
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e7000                                        
[    0.000000] PM: Registered nosave memory: 00000000000e7000 - 0000000000100000                                        
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)                                   
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data                                                           
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1                                                                
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259919                              
[    0.000000] Kernel command line: root=UUID=9bbd7a51-b386-44d8-adb7-b7a603cb1c4a ro quiet splash                      
[    0.000000] Enabling fast FPU save and restore... done.                                                              
[    0.000000] Enabling unmasked SIMD FPU exception support... done.                                                    
[    0.000000] Initializing CPU#0                                                                                       
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)                                                    
[    0.000000] Fast TSC calibration using PIT                                                                           
[    0.000000] Detected 1994.904 MHz processor.                                                                         
[    0.004000] spurious 8259A interrupt: IRQ7.                                                                          
[    0.004000] Console: colour VGA+ 80x25                                                                               
[    0.004000] console [tty0] enabled                                                                                   
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)                                         
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)                                           
[    0.004000] allocated 5241280 bytes of page_cgroup                                                                   
[    0.004000] please try cgroup_disable=memory option if you don't want                                                
[    0.004000] Scanning for low memory corruption every 60 seconds                                                      
[    0.004000] Memory: 1018340k/1048320k available (4115k kernel code, 29224k reserved, 2199k data, 532k init, 143112k highmem)                                                                                                                 
[    0.004000] virtual kernel memory layout:                                                                            
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                                                        
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                                                        
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)                                                        
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)                                                        
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)                                                        
[    0.004000]       .data : 0xc0504f5f - 0xc072ae60   (2199 kB)                                                        
[    0.004000]       .text : 0xc0100000 - 0xc0504f5f   (4115 kB)                                                        
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                              
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1                                  
[    0.004011] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.80 BogoMIPS (lpj=7979616)
[    0.004033] Security Framework initialized                                                                           
[    0.004043] SELinux:  Disabled at boot.                                                                              
[    0.004074] AppArmor: AppArmor initialized                                                                           
[    0.004083] Mount-cache hash table entries: 512                                                                      
[    0.004241] Initializing cgroup subsys ns                                                                            
[    0.004245] Initializing cgroup subsys cpuacct                                                                       
[    0.004247] Initializing cgroup subsys memory                                                                        
[    0.004252] Initializing cgroup subsys freezer                                                                       
[    0.004266] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)                                        
[    0.004269] CPU: L2 Cache: 1024K (64 bytes/line)                                                                     
[    0.004286] Checking 'hlt' instruction... OK.                                                                        
[    0.020669] SMP alternatives: switching to UP code                                                                   
[    0.138313] Freeing SMP alternatives: 18k freed                                                                      
[    0.138318] ACPI: Core revision 20080926                                                                             
[    0.139607] ACPI: Checking initramfs for custom DSDT                                                                 
[    0.420505] ..TIMER: vector=0x30 apic1=0 pin1=0 apic2=-1 pin2=-1                                                     
[    0.460208] CPU0: AMD Athlon(tm) 64 Processor 3200+ stepping 08                                                      
[    0.464001] Brought up 1 CPUs                                                                                        
[    0.464001] Total of 1 processors activated (3989.80 BogoMIPS).                                                      
[    0.464001] CPU0 attaching NULL sched-domain.                                                                        
[    0.464001] net_namespace: 776 bytes                                                                                 
[    0.464001] Booting paravirtualized kernel on bare hardware                                                          
[    0.464001] Time: 23:58:50  Date: 09/19/09                                                                           
[    0.464001] regulator: core version 0.5                                                                              
[    0.464001] NET: Registered protocol family 16                                                                       
[    0.464001] EISA bus registered                                                                                      
[    0.464001] ACPI: bus type pci registered                                                                            
[    0.464001] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=2                                                 
[    0.464001] PCI: Using configuration type 1 for base access                                                          
[    0.464001] ACPI: EC: Look up EC in DSDT                                                                             
[    0.465302] ACPI Warning (dsobject-0501): Package List length (5) larger than NumElements count (3), truncated       
[    0.465306]  [20080926]                                                                                              
[    0.467737] ACPI: Interpreter enabled                                                                                
[    0.467741] ACPI: (supports S0 S1 S3 S4 S5)                                                                          
[    0.467758] ACPI: Using IOAPIC for interrupt routing                                                                 
[    0.473827] ACPI: No dock devices found.                                                                             
[    0.473837] ACPI: PCI Root Bridge [PCI0] (0000:00)                                                                   
[    0.473888] pci 0000:00:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]                                             
[    0.473955] pci 0000:00:01.1: reg 20 io port: [0x5000-0x503f]                                                        
[    0.473959] pci 0000:00:01.1: reg 24 io port: [0x5040-0x507f]                                                        
[    0.473966] pci 0000:00:01.1: PME# supported from D3hot D3cold                                                       
[    0.473969] pci 0000:00:01.1: PME# disabled                                                                          
[    0.473987] pci 0000:00:02.0: reg 10 32bit mmio: [0xfebfb000-0xfebfbfff]                                             
[    0.474002] pci 0000:00:02.0: supports D1 D2                                                                         
[    0.474004] pci 0000:00:02.0: PME# supported from D0 D1 D2 D3hot D3cold                                              
[    0.474007] pci 0000:00:02.0: PME# disabled                                                                          
[    0.474021] pci 0000:00:02.1: reg 10 32bit mmio: [0xfebfc000-0xfebfcfff]                                             
[    0.474036] pci 0000:00:02.1: supports D1 D2                                                                         
[    0.474037] pci 0000:00:02.1: PME# supported from D0 D1 D2 D3hot D3cold                                              
[    0.474040] pci 0000:00:02.1: PME# disabled                                                                          
[    0.474058] pci 0000:00:02.2: reg 10 32bit mmio: [0xfebfdc00-0xfebfdcff]                                             
[    0.474073] pci 0000:00:02.2: supports D1 D2                                                                         
[    0.474075] pci 0000:00:02.2: PME# supported from D0 D1 D2 D3hot D3cold                                              
[    0.474078] pci 0000:00:02.2: PME# disabled                                                                          
[    0.474098] pci 0000:00:05.0: reg 10 32bit mmio: [0xfebfe000-0xfebfefff]                                             
[    0.474102] pci 0000:00:05.0: reg 14 io port: [0xeff0-0xeff7]                                                        
[    0.474116] pci 0000:00:05.0: supports D1 D2                                                                         
[    0.474117] pci 0000:00:05.0: PME# supported from D0 D1 D2 D3hot D3cold                                              
[    0.474120] pci 0000:00:05.0: PME# disabled                                                                          
[    0.474134] pci 0000:00:06.0: reg 10 io port: [0xe800-0xe8ff]                                                        
[    0.474138] pci 0000:00:06.0: reg 14 io port: [0xec00-0xec7f]                                                        
[    0.474142] pci 0000:00:06.0: reg 18 32bit mmio: [0xfebff000-0xfebfffff]                                             
[    0.474153] pci 0000:00:06.0: supports D1 D2                                                                         
[    0.474175] pci 0000:00:08.0: reg 20 io port: [0xffa0-0xffaf]                                                        
[    0.474290] pci 0000:02:05.0: reg 10 io port: [0xdfa0-0xdfaf]                                                        
[    0.474296] pci 0000:02:05.0: reg 14 io port: [0xdf90-0xdf9f]                                                        
[    0.474301] pci 0000:02:05.0: reg 18 io port: [0xdf80-0xdf8f]                                                        
[    0.474306] pci 0000:02:05.0: reg 1c io port: [0xdf60-0xdf6f]                                                        
[    0.474311] pci 0000:02:05.0: reg 20 io port: [0xdf40-0xdf5f]                                                        
[    0.474316] pci 0000:02:05.0: reg 24 io port: [0xd800-0xd8ff]                                                        
[    0.474321] pci 0000:02:05.0: reg 30 32bit mmio: [0xfeae0000-0xfeaeffff]                                             
[    0.474352] pci 0000:02:09.0: reg 10 32bit mmio: [0xfeaff800-0xfeafffff]                                             
[    0.474357] pci 0000:02:09.0: reg 14 32bit mmio: [0xfeaf8000-0xfeafbfff]                                             
[    0.474379] pci 0000:02:09.0: supports D1 D2                                                                         
[    0.474381] pci 0000:02:09.0: PME# supported from D0 D1 D2 D3hot                                                     
[    0.474384] pci 0000:02:09.0: PME# disabled                                                                          
[    0.474407] pci 0000:00:0a.0: bridge io port: [0xd000-0xdfff]                                                        
[    0.474410] pci 0000:00:0a.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]                                             
[    0.474442] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]                                             
[    0.474447] pci 0000:01:00.0: reg 14 32bit mmio: [0xe0000000-0xe7ffffff]                                             
[    0.474467] pci 0000:01:00.0: reg 30 32bit mmio: [0xfe9e0000-0xfe9fffff]                                             
[    0.474511] pci 0000:00:0b.0: bridge 32bit mmio: [0xfc900000-0xfe9fffff]                                             
[    0.474515] pci 0000:00:0b.0: bridge 32bit mmio pref: [0xdc800000-0xec7fffff]                                        
[    0.474523] bus 00 -> node 0                                                                                         
[    0.474528] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]                                                      
[    0.474693] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]                                                 
[    0.478008] ACPI: PCI Interrupt Link [LNKA] (IRQs 17) *0, disabled.                                                  
[    0.478176] ACPI: PCI Interrupt Link [LNKB] (IRQs 18) *0, disabled.                                                  
[    0.478343] ACPI: PCI Interrupt Link [LNKC] (IRQs 19) *10                                                            
[    0.478509] ACPI: PCI Interrupt Link [LNKD] (IRQs 17) *10                                                            
[    0.478675] ACPI: PCI Interrupt Link [LNKE] (IRQs 16) *11                                                            
[    0.478838] ACPI: PCI Interrupt Link [LUS0] (IRQs 20) *10                                                            
[    0.479000] ACPI: PCI Interrupt Link [LUS1] (IRQs 20) *11                                                            
[    0.479167] ACPI: PCI Interrupt Link [LUS2] (IRQs 20) *3                                                             
[    0.479333] ACPI: PCI Interrupt Link [LKLN] (IRQs 21) *5                                                             
[    0.479502] ACPI: PCI Interrupt Link [LAUI] (IRQs 21) *10                                                            
[    0.479668] ACPI: PCI Interrupt Link [LKMO] (IRQs 21) *0, disabled.                                                  
[    0.479831] ACPI: PCI Interrupt Link [LKSM] (IRQs 22) *0, disabled.                                                  
[    0.480004] ACPI: PCI Interrupt Link [LTID] (IRQs 22) *0, disabled.                                                  
[    0.480202] ACPI: PCI Interrupt Link [LATA] (IRQs 22) *14                                                            
[    0.480299] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 5F, should be 5A [20080926]            
[    0.480316] ACPI: WMI: Mapper loaded                                                                                 
[    0.480452] SCSI subsystem initialized                                                                               
[    0.480489] libata version 3.00 loaded.                                                                              
[    0.480527] usbcore: registered new interface driver usbfs                                                           
[    0.480541] usbcore: registered new interface driver hub                                                             
[    0.480564] usbcore: registered new device driver usb                                                                
[    0.480663] PCI: Using ACPI for IRQ routing                                                                          
[    0.480736] Bluetooth: Core ver 2.13                                                                                 
[    0.480736] NET: Registered protocol family 31                                                                       
[    0.480736] Bluetooth: HCI device and connection manager initialized                                                 
[    0.480736] Bluetooth: HCI socket layer initialized                                                                  
[    0.480736] NET: Registered protocol family 8                                                                        
[    0.480736] NET: Registered protocol family 20                                                                       
[    0.480736] NetLabel: Initializing                                                                                   
[    0.480736] NetLabel:  domain hash size = 128                                                                        
[    0.480736] NetLabel:  protocols = UNLABELED CIPSOv4                                                                 
[    0.480736] NetLabel:  unlabeled traffic allowed by default                                                          
[    0.480736] AppArmor: AppArmor Filesystem Enabled                                                                    
[    0.480736] pnp: PnP ACPI init                                                                                       
[    0.480736] ACPI: bus type pnp registered                                                                            
[    0.484347] pnp: PnP ACPI: found 13 devices                                                                          
[    0.484349] ACPI: ACPI bus type pnp unregistered                                                                     
[    0.484352] PnPBIOS: Disabled by ACPI PNP                                                                            
[    0.484362] system 00:06: ioport range 0x190-0x193 has been reserved                                                 
[    0.484365] system 00:06: ioport range 0x4d0-0x4d1 has been reserved                                                 
[    0.484371] system 00:07: iomem range 0xfec00000-0xfec00fff has been reserved                                        
[    0.484374] system 00:07: iomem range 0xfee00000-0xfeefffff could not be reserved                                    
[    0.484377] system 00:07: iomem range 0xff780000-0xff7bffff has been reserved                                        
[    0.484383] system 00:0b: ioport range 0x480-0x487 has been reserved                                                 
[    0.484385] system 00:0b: ioport range 0xd00-0xd7f has been reserved                                                 
[    0.484390] system 00:0c: iomem range 0x0-0x9ffff could not be reserved                                              
[    0.484393] system 00:0c: iomem range 0xc0000-0xdffff could not be reserved                                          
[    0.484396] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved                                          
[    0.484398] system 00:0c: iomem range 0x100000-0x3fffffff could not be reserved                                      
[    0.484401] system 00:0c: iomem range 0xff7c0000-0xffffffff has been reserved                                        
[    0.519091] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:02                                                      
[    0.519094] pci 0000:00:0a.0:   IO window: 0xd000-0xdfff                                                             
[    0.519097] pci 0000:00:0a.0:   MEM window: 0xfea00000-0xfeafffff                                                    
[    0.519100] pci 0000:00:0a.0:   PREFETCH window: disabled                                                            
[    0.519103] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:01                                                      
[    0.519105] pci 0000:00:0b.0:   IO window: disabled                                                                  
[    0.519110] pci 0000:00:0b.0:   MEM window: 0xfc900000-0xfe9fffff                                                    
[    0.519114] pci 0000:00:0b.0:   PREFETCH window: 0x000000dc800000-0x000000ec7fffff                                   
[    0.519124] pci 0000:00:0a.0: setting latency timer to 64                                                            
[    0.519129] bus: 00 index 0 io port: [0x00-0xffff]                                                                   
[    0.519131] bus: 00 index 1 mmio: [0x000000-0xffffffff]                                                              
[    0.519134] bus: 02 index 0 io port: [0xd000-0xdfff]                                                                 
[    0.519136] bus: 02 index 1 mmio: [0xfea00000-0xfeafffff]                                                            
[    0.519138] bus: 02 index 2 mmio: [0x0-0x0]                                                                          
[    0.519140] bus: 02 index 3 mmio: [0x0-0x0]                                                                          
[    0.519141] bus: 01 index 0 mmio: [0x0-0x0]                                                                          
[    0.519143] bus: 01 index 1 mmio: [0xfc900000-0xfe9fffff]                                                            
[    0.519145] bus: 01 index 2 mmio: [0xdc800000-0xec7fffff]                                                            
[    0.519147] bus: 01 index 3 mmio: [0x0-0x0]                                                                          
[    0.519155] NET: Registered protocol family 2                                                                        
[    0.519258] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)                                        
[    0.519596] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                     
[    0.520697] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)                                              
[    0.521256] TCP: Hash tables configured (established 131072 bind 65536)                                              
[    0.521259] TCP reno registered                                                                                      
[    0.521377] NET: Registered protocol family 1                                                                        
[    0.521522] checking if image is initramfs... it is                                                                  
[    1.020063] Switched to high resolution mode on CPU 0                                                                
[    1.111258] Freeing initrd memory: 7357k freed                                                                       
[    1.111360] cpufreq: No nForce2 chipset.                                                                             
[    1.111508] audit: initializing netlink socket (disabled)                                                            
[    1.111527] type=2000 audit(1253404731.108:1): initialized                                                           
[    1.119355] highmem bounce pool size: 64 pages                                                                       
[    1.119361] HugeTLB registered 4 MB page size, pre-allocated 0 pages                                                 
[    1.120505] VFS: Disk quotas dquot_6.5.1                                                                             
[    1.120555] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)                                               
[    1.121083] fuse init (API version 7.10)                                                                             
[    1.121159] msgmni has been set to 1724                                                                              
[    1.121337] alg: No test for stdrng (krng)                                                                           
[    1.121347] io scheduler noop registered                                                                             
[    1.121349] io scheduler anticipatory registered                                                                     
[    1.121351] io scheduler deadline registered                                                                         
[    1.121365] io scheduler cfq registered (default)                                                                    
[    1.152069] pci 0000:01:00.0: Boot video device                                                                      
[    1.155539] pci_hotplug: PCI Hot Plug PCI Core version: 0.5                                                          
[    1.155546] pciehp: PCI Express Hot Plug Controller Driver version: 0.4                                              
[    1.155664] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0                                
[    1.155667] ACPI: Power Button (FF) [PWRF]                                                                           
[    1.155709] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1                       
[    1.155711] ACPI: Power Button (CM) [PWRB]                                                                           
[    1.155827] ACPI: processor limited to max C-state 1                                                                 
[    1.155849] processor ACPI_CPU:00: registered as cooling_device0                                                     
[    1.157979] isapnp: Scanning for PnP cards...                                                                        
[    1.511515] isapnp: No Plug & Play device found                                                                      
[    1.512499] Serial: 8250/16550 driver4 ports, IRQ sharing enabled                                                    
[    1.512580] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                     
[    1.512850] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                                                          
[    1.513531] brd: module loaded                                                                                       
[    1.513823] loop: module loaded                                                                                      
[    1.513890] Fixed MDIO Bus: probed                                                                                   
[    1.513896] PPP generic driver version 2.4.2                                                                         
[    1.513945] input: Macintosh mouse button emulation as /devices/virtual/input/input2                                 
[    1.513969] Driver 'sd' needs updating - please use bus_type methods                                                 
[    1.513977] Driver 'sr' needs updating - please use bus_type methods                                                 
[    1.514099] sata_via 0000:02:05.0: version 2.4                                                                       
[    1.514371] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 19                                                        
[    1.514382] sata_via 0000:02:05.0: PCI INT A -> Link[LNKC] -> GSI 19 (level, high) -> IRQ 19                         
[    1.514437] sata_via 0000:02:05.0: routed to hard irq line 10                                                        
[    1.514519] scsi0 : sata_via                                                                                         
[    1.514590] scsi1 : sata_via                                                                                         
[    1.514639] scsi2 : sata_via                                                                                         
[    1.514670] ata1: SATA max UDMA/133 port i16@0xdfa0 bmdma 0xdf40 irq 19                                              
[    1.514673] ata2: SATA max UDMA/133 port i16@0xdf90 bmdma 0xdf48 irq 19                                              
[    1.514676] ata3: PATA max UDMA/133 port i16@0xdf80 bmdma 0xdf50 irq 19                                              
[    1.842583] ata1: SATA link down (SStatus 0 SControl 310)                                                            
[    2.170581] ata2: SATA link down (SStatus 0 SControl 310)                                                            
[    2.335253] pata_amd 0000:00:08.0: version 0.3.10                                                                    
[    2.335294] pata_amd 0000:00:08.0: setting latency timer to 64                                                       
[    2.335352] scsi3 : pata_amd                                                                                         
[    2.335408] scsi4 : pata_amd                                                                                         
[    2.336642] ata4: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14                                          
[    2.336645] ata5: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15                                          
[    2.556264] ata4.00: ATA-6: ST3200822A, 3.01, max UDMA/100                                                           
[    2.556267] ata4.00: 390721968 sectors, multi 16: LBA48                                                              
[    2.556290] ata4: nv_mode_filter: 0x3f39f&0x3f01f->0x3f01f, BIOS=0x3f000 (0xc600c000) ACPI=0x3f01f (17:900:0x11)     
[    2.572207] ata4.00: configured for UDMA/100                                                                         
[    2.736256] ata5.00: ATAPI: TSSTcorp CDDVDW SH-S202N, SB02, max UDMA/66                                              
[    2.736279] ata5: nv_mode_filter: 0x1f39f&0x707f->0x701f, BIOS=0x7000 (0xc600c000) ACPI=0x7000 (54:900:0x11)         
[    2.752210] ata5.00: configured for UDMA/33                                                                          
[    2.756866] scsi 3:0:0:0: Direct-Access     ATA      ST3200822A       3.01 PQ: 0 ANSI: 5                             
[    2.756951] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)                                  
[    2.756967] sd 3:0:0:0: [sda] Write Protect is off                                                                   
[    2.756969] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                
[    2.756991] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                  
[    2.757043] sd 3:0:0:0: [sda] 390721968 512-byte hardware sectors: (200 GB/186 GiB)                                  
[    2.757055] sd 3:0:0:0: [sda] Write Protect is off                                                                   
[    2.757058] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00                                                                
[    2.757078] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                  
[    2.757081]  sda: sda1 sda2 < sda5 sda6 >                                                                            
[    2.774358] sd 3:0:0:0: [sda] Attached SCSI disk                                                                     
[    2.774397] sd 3:0:0:0: Attached scsi generic sg0 type 0                                                             
[    2.776830] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S202N  SB02 PQ: 0 ANSI: 5                             
[    2.779988] sr0: scsi3-mmc drive: 125x/125x writer dvd-ram cd/rw xa/form2 cdda tray                                  
[    2.779992] Uniform CD-ROM driver Revision: 3.20                                                                     
[    2.780064] sr 4:0:0:0: Attached scsi CD-ROM sr0                                                                     
[    2.780100] sr 4:0:0:0: Attached scsi generic sg1 type 5                                                             
[    2.780475] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver                                               
[    2.780727] ACPI: PCI Interrupt Link [LUS2] enabled at IRQ 20                                                        
[    2.780733] ehci_hcd 0000:00:02.2: PCI INT C -> Link[LUS2] -> GSI 20 (level, high) -> IRQ 20                         
[    2.780756] ehci_hcd 0000:00:02.2: setting latency timer to 64                                                       
[    2.780759] ehci_hcd 0000:00:02.2: EHCI Host Controller                                                              
[    2.780825] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 1                                     
[    2.780854] ehci_hcd 0000:00:02.2: debug port 1                                                                      
[    2.780858] ehci_hcd 0000:00:02.2: cache line size of 64 is not supported                                            
[    2.780872] ehci_hcd 0000:00:02.2: irq 20, io mem 0xfebfdc00                                                         
[    2.792007] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00                                                        
[    2.792082] usb usb1: configuration #1 chosen from 1 choice                                                          
[    2.792110] hub 1-0:1.0: USB hub found                                                                               
[    2.792121] hub 1-0:1.0: 6 ports detected                                                                            
[    2.792216] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver                                                   
[    2.792454] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20                                                        
[    2.792458] ohci_hcd 0000:00:02.0: PCI INT A -> Link[LUS0] -> GSI 20 (level, high) -> IRQ 20                         
[    2.792467] ohci_hcd 0000:00:02.0: setting latency timer to 64                                                       
[    2.792469] ohci_hcd 0000:00:02.0: OHCI Host Controller                                                              
[    2.792506] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2                                     
[    2.792519] ohci_hcd 0000:00:02.0: irq 20, io mem 0xfebfb000                                                         
[    2.850049] usb usb2: configuration #1 chosen from 1 choice                                                          
[    2.850070] hub 2-0:1.0: USB hub found                                                                               
[    2.850079] hub 2-0:1.0: 3 ports detected                                                                            
[    2.850372] ACPI: PCI Interrupt Link [LUS1] enabled at IRQ 20                                                        
[    2.850375] ohci_hcd 0000:00:02.1: PCI INT B -> Link[LUS1] -> GSI 20 (level, high) -> IRQ 20                         
[    2.850384] ohci_hcd 0000:00:02.1: setting latency timer to 64                                                       
[    2.850387] ohci_hcd 0000:00:02.1: OHCI Host Controller                                                              
[    2.850430] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3                                     
[    2.850441] ohci_hcd 0000:00:02.1: irq 20, io mem 0xfebfc000                                                         
[    2.906034] usb usb3: configuration #1 chosen from 1 choice                                                          
[    2.906054] hub 3-0:1.0: USB hub found                                                                               
[    2.906063] hub 3-0:1.0: 3 ports detected                                                                            
[    2.906137] uhci_hcd: USB Universal Host Controller Interface driver                                                 
[    2.906198] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12                                   
[    2.908473] serio: i8042 KBD port at 0x60,0x64 irq 1                                                                 
[    2.908477] serio: i8042 AUX port at 0x60,0x64 irq 12                                                                
[    2.908569] mice: PS/2 mouse device common for all mice                                                              
[    2.908679] rtc_cmos 00:02: RTC can wake from S4                                                                     
[    2.908712] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0                                                    
[    2.908735] rtc0: alarms up to one year, y3k, 114 bytes nvram                                                        
[    2.908790] device-mapper: uevent: version 1.0.3                                                                     
[    2.908880] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]                         
[    2.908924] device-mapper: multipath: version 1.0.5 loaded                                                           
[    2.908927] device-mapper: multipath round-robin: version 1.0.0 loaded                                               
[    2.908994] EISA: Probing bus 0 at eisa.0                                                                            
[    2.909007] Cannot allocate resource for EISA slot 4                                                                 
[    2.909010] Cannot allocate resource for EISA slot 5                                                                 
[    2.909017] EISA: Detected 0 cards.                                                                                  
[    2.909042] cpuidle: using governor ladder                                                                           
[    2.909044] cpuidle: using governor menu                                                                             
[    2.909503] TCP cubic registered                                                                                     
[    2.909590] NET: Registered protocol family 10                                                                       
[    2.909959] lo: Disabled Privacy Extensions                                                                          
[    2.910242] NET: Registered protocol family 17                                                                       
[    2.910256] Bluetooth: L2CAP ver 2.11                                                                                
[    2.910258] Bluetooth: L2CAP socket layer initialized                                                                
[    2.910261] Bluetooth: SCO (Voice Link) ver 0.6                                                                      
[    2.910262] Bluetooth: SCO socket layer initialized                                                                  
[    2.910284] Bluetooth: RFCOMM socket layer initialized                                                               
[    2.910292] Bluetooth: RFCOMM TTY layer initialized                                                                  
[    2.910294] Bluetooth: RFCOMM ver 1.10                                                                               
[    2.910313] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3200+ processors (1 cpu cores) (version 2.20.00)        
[    2.910345] powernow-k8:    0 : fid 0xc (2000 MHz), vid 0x2                                                          
[    2.910348] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x6                                                          
[    2.910350] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0xa                                                           
[    2.910380] powernow-k8: ph2 null fid transition 0xc                                                                 
[    2.910448] Using IPI No-Shortcut mode                                                                               
[    2.910509] registered taskstats version 1                                                                           
[    2.910615]   Magic number: 9:330:1010                                                                               
[    2.910689] rtc_cmos 00:02: setting system clock to 2009-09-19 23:58:53 UTC (1253404733)                             
[    2.910692] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found                                                     
[    2.910693] EDD information not available.                                                                           
[    2.911244] Freeing unused kernel memory: 532k freed                                                                 
[    2.911365] Write protecting the kernel text: 4116k                                                                  
[    2.911406] Write protecting the kernel read-only data: 1528k                                                        
[    2.945577] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3                       
[    3.216026] usb 1-6: new high speed USB device using ehci_hcd and address 3                                          
[    3.357495] usb 1-6: configuration #1 chosen from 1 choice                                                           
[    3.512335] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.                                      
[    3.512352] forcedeth 0000:00:05.0: enabling device (0005 -> 0007)                                                   
[    3.512652] ACPI: PCI Interrupt Link [LKLN] enabled at IRQ 21                                                        
[    3.512664] forcedeth 0000:00:05.0: PCI INT A -> Link[LKLN] -> GSI 21 (level, high) -> IRQ 21                        
[    3.512669] forcedeth 0000:00:05.0: setting latency timer to 64                                                      
[    3.512734] nv_probe: set workaround bit for reversed mac addr                                                       
[    3.556730] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 17                                                        
[    3.556744] ohci1394 0000:02:09.0: PCI INT A -> Link[LNKD] -> GSI 17 (level, high) -> IRQ 17                         
[    3.606543] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]                                                                                                             
[    3.664033] usb 2-2: new full speed USB device using ohci_hcd and address 2                                          
[    3.889256] usb 2-2: configuration #1 chosen from 1 choice                                                           
[    3.908716] Initializing USB Mass Storage driver...                                                                  
[    3.910235] scsi5 : SCSI emulation for USB Mass Storage devices                                                      
[    3.910999] usb-storage: device found at 3                                                                           
[    3.911001] usb-storage: waiting for device to settle before scanning                                                
[    3.911255] scsi6 : SCSI emulation for USB Mass Storage devices                                                      
[    3.911866] usbcore: registered new interface driver usb-storage                                                     
[    3.911870] USB Mass Storage support registered.                                                                     
[    3.912126] usb-storage: device found at 2                                                                           
[    3.912128] usb-storage: waiting for device to settle before scanning                                                
[    4.032897] forcedeth 0000:00:05.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:0e:a6:94:d5:bc                           
[    4.032903] forcedeth 0000:00:05.0: timirq lnktim desc-v1                                                            
[    4.214714] PM: Starting manual resume from disk                                                                     
[    4.214718] PM: Resume from partition 8:5                                                                            
[    4.214720] PM: Checking hibernation image.                                                                          
[    4.214968] PM: Resume from disk failed.                                                                             
[    4.217615] EXT4-fs: INFO: recovery required on readonly filesystem.                                                 
[    4.217619] EXT4-fs: write access will be enabled during recovery.                                                   
[    4.243174] EXT4-fs: barriers enabled                                                                                
[    4.888899] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000069008c]                                          
[    5.765225] kjournald2 starting.  Commit interval 5 seconds                                                          
[    5.765244] EXT4-fs: delayed allocation enabled                                                                      
[    5.765246] EXT4-fs: file extents enabled                                                                            
[    5.765393] EXT4-fs: mballoc enabled                                                                                 
[    5.765396] EXT4-fs: sda1: orphan cleanup on readonly fs                                                             
[    5.765402] ext4_orphan_cleanup: deleting unreferenced inode 5978                                                    
[    5.765434] ext4_orphan_cleanup: deleting unreferenced inode 6900                                                    
[    5.765442] ext4_orphan_cleanup: deleting unreferenced inode 2063                                                    
[    5.765449] EXT4-fs: sda1: 3 orphan inodes deleted                                                                   
[    5.765451] EXT4-fs: recovery complete.                                                                              
[    5.952469] EXT4-fs: mounted filesystem with ordered data mode.                                                      
[    8.908229] usb-storage: device scan complete                                                                        
[    8.908699] scsi 5:0:0:0: Direct-Access     Initio   WD5000AAKB-00YSA 1.06 PQ: 0 ANSI: 0                             
[    8.909556] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                  
[    8.910428] sd 5:0:0:0: [sdb] Write Protect is off                                                                   
[    8.910431] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00                                                                
[    8.910433] sd 5:0:0:0: [sdb] Assuming drive cache: write through                                                    
[    8.911053] sd 5:0:0:0: [sdb] 976773168 512-byte hardware sectors: (500 GB/465 GiB)                                  
[    8.911927] sd 5:0:0:0: [sdb] Write Protect is off                                                                   
[    8.911930] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00                                                                
[    8.911932] sd 5:0:0:0: [sdb] Assuming drive cache: write through                                                    
[    8.911935]  sdb: sdb1                                                                                               
[    8.912534] sd 5:0:0:0: [sdb] Attached SCSI disk                                                                     
[    8.912590] sd 5:0:0:0: Attached scsi generic sg2 type 0                                                             
[    8.913323] usb-storage: device scan complete                                                                        
[    8.920324] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0                             
[    8.927325] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0                             
[    8.934323] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0                             
[    8.941324] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0                             
[    8.988383] sd 6:0:0:0: [sdc] Attached SCSI removable disk                                                           
[    8.988417] sd 6:0:0:0: Attached scsi generic sg3 type 0                                                             
[    9.035371] sd 6:0:0:1: [sdd] Attached SCSI removable disk                                                           
[    9.035404] sd 6:0:0:1: Attached scsi generic sg4 type 0                                                             
[    9.082373] sd 6:0:0:2: [sde] Attached SCSI removable disk                                                           
[    9.082405] sd 6:0:0:2: Attached scsi generic sg5 type 0                                                             
[    9.129376] sd 6:0:0:3: [sdf] Attached SCSI removable disk                                                           
[    9.129411] sd 6:0:0:3: Attached scsi generic sg6 type 0                                                             
[   10.766502] udev: starting version 141                                                                               
[   10.836803] parport_pc 00:05: reported by Plug and Play ACPI                                                         
[   10.836877] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]                        
[   10.879802] Linux agpgart interface v0.103                                                                           
[   10.882225] agpgart-amd64 0000:00:00.0: AGP bridge [10de/00d1]                                                       
[   10.882255] agpgart-amd64 0000:00:00.0: setting up Nforce3 AGP                                                       
[   10.890578] agpgart-amd64 0000:00:00.0: AGP aperture is 128M @ 0xf0000000                                            
[   10.893311] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000                                                       
[   10.893348] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x5040                                                       
[   11.109926] ACPI: PCI Interrupt Link [LAUI] enabled at IRQ 21                                                        
[   11.109934] Intel ICH 0000:00:06.0: PCI INT A -> Link[LAUI] -> GSI 21 (level, high) -> IRQ 21                        
[   11.110046] Intel ICH 0000:00:06.0: setting latency timer to 64                                                      
[   11.182888] end_request: I/O error, dev sr0, sector 0                                                                
[   11.182896] Buffer I/O error on device sr0, logical block 0                                                          
[   11.184993] input: PC Speaker as /devices/platform/pcspkr/input/input4                                               
[   11.189043] end_request: I/O error, dev sr0, sector 0                                                                
[   11.189050] Buffer I/O error on device sr0, logical block 0                                                          
[   11.262398] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume                  
[   11.432055] intel8x0_measure_ac97_clock: measured 52787 usecs                                                        
[   11.432060] intel8x0: clocking to 48000                                                                              
[   11.433812] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4                                             
[   11.489641] ppdev: user-space parallel port driver                                                                   
[   11.704908] nvidia: module license 'NVIDIA' taints kernel.                                                           
[   11.961605] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 16                                                        
[   11.961619] nvidia 0000:01:00.0: PCI INT A -> Link[LNKE] -> GSI 16 (level, high) -> IRQ 16                           
[   11.962782] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.20  Thu Jun 25 19:23:24 PDT 2009                     
[   12.024608] psmouse serio1: ID: 10 00 64<6>lp0: using parport0 (interrupt-driven).                                   
[   12.098235] logips2pp: Detected unknown logitech mouse model 62                                                      
[   12.181535] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k                                
[   12.609935] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input5                   
[   12.716940] EXT4 FS on sda1, internal journal on sda1:8                                                              
[   17.974149] EXT4-fs: barriers enabled                                                                                
[   17.985639] kjournald2 starting.  Commit interval 5 seconds
[   18.004576] EXT4 FS on sda6, internal journal on sda6:8
[   18.004579] EXT4-fs: delayed allocation enabled
[   18.004581] EXT4-fs: file extents enabled
[   18.006005] EXT4-fs: mballoc enabled
[   18.006011] EXT4-fs: mounted filesystem with ordered data mode.
[   18.220656] type=1505 audit(1253404748.809:2): operation="profile_load" name="/sbin/dhclient-script" name2="default"pid=2126
[   18.220833] type=1505 audit(1253404748.809:3): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2126
[   18.220886] type=1505 audit(1253404748.809:4): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2126
[   18.220933] type=1505 audit(1253404748.809:5): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2126
[   18.409273] type=1505 audit(1253404748.997:6): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2137
[   18.409529] type=1505 audit(1253404748.997:7): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2137
[   18.441366] type=1505 audit(1253404749.029:8): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2141
[   18.731281] RPC: Registered udp transport module.
[   18.731285] RPC: Registered tcp transport module.
[   18.854943] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[   20.061420] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   20.077385] NFSD: starting 90-second grace period
[   21.834021] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.834025] Bluetooth: BNEP filters: protocol multicast
[   21.842026] Bridge firewalling registered
[/quote]

[quote=Xorg.0.log]
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux htpc 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686
Build Date: 09 April 2009  02:10:02AM                                                                  
xorg-server 2:1.6.0-0ubuntu14 (buildd@rothera.buildd)                                                  
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)                                             
        to make sure that you have the latest version.                                                 
Markers: (--) probed, (**) from config file, (==) default setting,                                     
        (++) from command line, (!!) notice, (II) informational,                                       
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.                                  
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Sep 19 19:59:13 2009                                   
(==) Using config file: "/etc/X11/xorg.conf"                                                           
(==) ServerLayout "Layout0"                                                                            
(**) |-->Screen "Screen0" (0)                                                                          
(**) |   |-->Monitor "Monitor0"                                                                        
(**) |   |-->Device "Device0"                                                                          
(**) |-->Input Device "Keyboard0"                                                                      
(**) |-->Input Device "Mouse0"                                                                         
(**) Option "DontZap" "True"                                                                           
(==) Automatically adding devices                                                                      
(==) Automatically enabling devices                                                                    
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.                                     
        Entry deleted from font path.                                                                  
(==) FontPath set to:                                                                                  
        /usr/share/fonts/X11/misc,                                                                     
        /usr/share/fonts/X11/100dpi/:unscaled,                                                         
        /usr/share/fonts/X11/75dpi/:unscaled,                                                          
        /usr/share/fonts/X11/Type1,                                                                    
        /usr/share/fonts/X11/100dpi,                                                                   
        /usr/share/fonts/X11/75dpi,                                                                    
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,                                              
        built-ins                                                                                      
(==) ModulePath set to "/usr/lib/xorg/modules"                                                         
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.        
(WW) Disabling Keyboard0                                                                               
(WW) Disabling Mouse0                                                                                  
(II) Loader magic: 0x3bc0                                                                              
(II) Module ABI versions:                                                                              
        X.Org ANSI C Emulation: 0.4                                                                    
        X.Org Video Driver: 5.0                                                                        
        X.Org XInput driver : 4.0                                                                      
        X.Org Server Extension : 2.0                                                                   
(II) Loader running on linux                                                                           
(++) using VT number 7                                                                                 

(--) PCI:*(0@1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/16777216, 0xe0000000/134217728, BIOS @ 0x????????/131072                                                                                                
(II) Open ACPI successful (/var/run/acpid.socket)                                                                       
(II) System resource ranges:                                                                                            
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
(II) LoadModule: "extmod"                                                                                               
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so                                                             
(II) Module extmod: vendor="X.Org Foundation"                                                                           
        compiled for 1.6.0, module version = 1.0.0                                                                      
        Module class: X.Org Server Extension                                                                            
        ABI class: X.Org Server Extension, version 2.0                                                                  
(II) Loading extension MIT-SCREEN-SAVER                                                                                 
(II) Loading extension XFree86-VidModeExtension                                                                         
(II) Loading extension XFree86-DGA                                                                                      
(II) Loading extension DPMS                                                                                             
(II) Loading extension XVideo                                                                                           
(II) Loading extension XVideo-MotionCompensation                                                                        
(II) Loading extension X-Resource                                                                                       
(II) LoadModule: "dbe"                                                                                                  
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so                                                                
(II) Module dbe: vendor="X.Org Foundation"                                                                              
        compiled for 1.6.0, module version = 1.0.0                                                                      
        Module class: X.Org Server Extension                                                                            
        ABI class: X.Org Server Extension, version 2.0                                                                  
(II) Loading extension DOUBLE-BUFFER                                                                                    
(II) LoadModule: "glx"                                                                                                  
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so                                                                
(II) Module glx: vendor="NVIDIA Corporation"                                                                            
        compiled for 4.0.2, module version = 1.0.0                                                                      
        Module class: X.Org Server Extension                                                                            
(II) NVIDIA GLX Module  173.14.20  Thu Jun 25 19:49:59 PDT 2009                                                         
(II) Loading extension GLX                                                                                              
(II) LoadModule: "record"                                                                                               
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so                                                             
(II) Module record: vendor="X.Org Foundation"                                                                           
        compiled for 1.6.0, module version = 1.13.0                                                                     
        Module class: X.Org Server Extension                                                                            
        ABI class: X.Org Server Extension, version 2.0                                                                  
(II) Loading extension RECORD                                                                                           
(II) LoadModule: "dri"                                                                                                  
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so                                                                
(II) Module dri: vendor="X.Org Foundation"                                                                              
        compiled for 1.6.0, module version = 1.0.0                                                                      
        ABI class: X.Org Server Extension, version 2.0                                                                  
(II) Loading extension XFree86-DRI                                                                                      
(II) LoadModule: "dri2"                                                                                                 
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so                                                               
(II) Module dri2: vendor="X.Org Foundation"                                                                             
        compiled for 1.6.0, module version = 1.0.0                                                                      
        ABI class: X.Org Server Extension, version 2.0                                                                  
(II) Loading extension DRI2                                                                                             
(II) LoadModule: "nvidia"                                                                                               
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so                                                               
(II) Module nvidia: vendor="NVIDIA Corporation"                                                                         
        compiled for 4.0.2, module version = 1.0.0                                                                      
        Module class: X.Org Video Driver                                                                                
(II) NVIDIA dlloader X Driver  173.14.20  Thu Jun 25 19:28:52 PDT 2009                                                  
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs                                                                
(II) Primary Device is: PCI 01@00:00:0                                                                                  
(II) Loading sub module "fb"                                                                                            
(II) LoadModule: "fb"                                                                                                   
(II) Loading /usr/lib/xorg/modules//libfb.so                                                                            
(II) Module fb: vendor="X.Org Foundation"                                                                               
        compiled for 1.6.0, module version = 1.0.0                                                                      
        ABI class: X.Org ANSI C Emulation, version 0.4                                                                  
(II) Loading sub module "wfb"                                                                                           
(II) LoadModule: "wfb"                                                                                                  
(II) Loading /usr/lib/xorg/modules//libwfb.so                                                                           
(II) Module wfb: vendor="X.Org Foundation"                                                                              
        compiled for 1.6.0, module version = 1.0.0                                                                      
        ABI class: X.Org ANSI C Emulation, version 0.4                                                                  
(II) Loading sub module "ramdac"                                                                                        
(II) LoadModule: "ramdac"                                                                                               
(II) Module "ramdac" already built-in                                                                                   
(II) resource ranges after probing:                                                                                     
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32                                                                       
(==) NVIDIA(0): RGB weight 888                                                                                          
(==) NVIDIA(0): Default visual is TrueColor                                                                             
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)                                                                  
(**) NVIDIA(0): Enabling RENDER acceleration                                                                            
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is                                           
(II) NVIDIA(0):     enabled.                                                                                            
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)                                                  
(--) NVIDIA(0): Memory: 131072 kBytes                                                                                   
(--) NVIDIA(0): VideoBIOS: 04.34.20.42.37                                                                               
(II) NVIDIA(0): Detected AGP rate: 8X                                                                                   
(--) NVIDIA(0): Interlaced video modes are supported on this GPU                                                        
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:                                            
(--) NVIDIA(0):     SANYO LCD (CRT-0)                                                                                   
(--) NVIDIA(0): SANYO LCD (CRT-0): 350.0 MHz maximum pixel clock                                                        
(II) NVIDIA(0): Assigned Display Device: CRT-0                                                                          
(==) NVIDIA(0):                                                                                                         
(==) NVIDIA(0): No modes were requested said:**
>  -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [16] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                                             
        [17] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                                         
        [18] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                                         
        [19] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                                         
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [24] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [25] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [26] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [27] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
        [28] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                                             
        [29] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                                             
(II) NVIDIA(0): Initialized AGP GART.                                                                                   
(II) NVIDIA(0): Setting mode "nvidia-auto-select"                                                                       
(II) Loading extension NV-GLX                                                                                           
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized                                                         
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture                                                           
(==) NVIDIA(0): Backing store disabled                                                                                  
(==) NVIDIA(0): Silken mouse enabled                                                                                    
(**) Option "dpms"                                                                                                      
(**) NVIDIA(0): DPMS enabled                                                                                            
(II) Loading extension NV-CONTROL                                                                                       
(==) RandR enabled                                                                                                      
(II) Initializing built-in extension Generic Event Extension                                                            
(II) Initializing built-in extension SHAPE                                                                              
(II) Initializing built-in extension MIT-SHM                                                                            
(II) Initializing built-in extension XInputExtension                                                                    
(II) Initializing built-in extension XTEST                                                                              
(II) Initializing built-in extension BIG-REQUESTS                                                                       
(II) Initializing built-in extension SYNC                                                                               
(II) Initializing built-in extension XKEYBOARD                                                                          
(II) Initializing built-in extension XC-MISC                                                                            
(II) Initializing built-in extension SECURITY                                                                           
(II) Initializing built-in extension XINERAMA                                                                           
(II) Initializing built-in extension XFIXES                                                                             
(II) Initializing built-in extension RENDER                                                                             
(II) Initializing built-in extension RANDR                                                                              
(II) Initializing built-in extension COMPOSITE                                                                          
(II) Initializing built-in extension DAMAGE                                                                             
(II) Initializing extension GLX                                                                                         
(II) config/hal: Adding input device Macintosh mouse button emulation                                                   
(II) LoadModule: "evdev"                                                                                                
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so                                                                  
(II) Module evdev: vendor="X.Org Foundation"                                                                            
        compiled for 1.6.0, module version = 2.1.1                                                                      
        Module class: X.Org XInput Driver                                                                               
        ABI class: X.Org XInput driver, version 4.0                                                                     
(**) Macintosh mouse button emulation: always reports core events                                                       
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"                                                      
(II) Macintosh mouse button emulation: Found 3 mouse buttons                                                            
(II) Macintosh mouse button emulation: Found x and y relative axes                                                      
(II) Macintosh mouse button emulation: Configuring as mouse                                                             
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5                                                    
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200         
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)                              
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1                                            
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device ImExPS/2 Logitech Explorer Mouse
(**) ImExPS/2 Logitech Explorer Mouse: always reports core events
(**) ImExPS/2 Logitech Explorer Mouse: Device: "/dev/input/event5"
(II) ImExPS/2 Logitech Explorer Mouse: Found 5 mouse buttons
(II) ImExPS/2 Logitech Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Logitech Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Logitech Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Logitech Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Logitech Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Logitech Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Logitech Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Logitech Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Logitech Explorer Mouse: (accel) set acceleration profile 0


---

### Post by MiiJaySung on 2009-11-02
Ditto, same here. 

You have an nForce chipset right?

I dunno what exactly is the root of this, all I will say is disabling ACPI with acpi=off in your grub kernel line will stop this at the cost of not being able to suspend/hibernate etc.

---

