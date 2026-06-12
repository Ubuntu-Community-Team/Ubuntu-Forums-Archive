---
title: "URGENT! No internet after power failure"
date: 2009-02-10
forum: General Help
---

### Post by Thanh-BKK on 2009-02-10
Hello.

Yesterday i had a power failure (UPS failed due to dead battery or something, PC shut off) and ever since when i shut down Ubuntu i get these error messages again (something with network manager) like after i first installed it....

And now (much worse!!) i can no longer do anything but use Firefox on the internet! I.e. no Thunderbird, no torrents, not even Synaptic - everything "times out" however Firefox is fine!

What can i do to fix this, please... it is really urgent.

Many thanks in advance.

Thanh

PS Ubuntu 8.04.1 Hardy, Kernel 2.6.24-21 generic, Gnome 2.22.3

---

### Post by pytheas22 on 2009-02-10
Please open a terminal, run these commands and post the output:
```

ping -c 5 google.com
wget google.com
sudo apt-get update
dmesg
```

The last command will dump a lot of output, but please post it all.

---

### Post by Thanh-BKK on 2009-02-10
Ok here goes:

thanh@thanh-desktop:~$ ping -c 5 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from google.com (74.125.45.100): icmp_seq=1 ttl=235 time=276 ms
64 bytes from google.com (74.125.45.100): icmp_seq=2 ttl=235 time=277 ms
64 bytes from google.com (74.125.45.100): icmp_seq=3 ttl=235 time=275 ms
64 bytes from google.com (74.125.45.100): icmp_seq=4 ttl=235 time=275 ms
64 bytes from google.com (74.125.45.100): icmp_seq=5 ttl=235 time=276 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 275.000/276.263/277.347/1.104 ms


thanh@thanh-desktop:~$ ping -c 5 google.com
PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from google.com (74.125.45.100): icmp_seq=1 ttl=235 time=276 ms
64 bytes from google.com (74.125.45.100): icmp_seq=2 ttl=235 time=277 ms
64 bytes from google.com (74.125.45.100): icmp_seq=3 ttl=235 time=275 ms
64 bytes from google.com (74.125.45.100): icmp_seq=4 ttl=235 time=275 ms
64 bytes from google.com (74.125.45.100): icmp_seq=5 ttl=235 time=276 ms

--- google.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 275.000/276.263/277.347/1.104 ms


thanh@thanh-desktop:~$ sudo apt-get update
[sudo] password for thanh: 
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US      
Get:2 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy Release.gpg [189B]          
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main Translation-en_US        
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                      
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/restricted Translation-en_US  
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/multiverse Translation-en_US
Get:4 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates Release.gpg [189B]
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                    
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy Release                           
Get:6 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates Release [58.5kB]             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                     
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main Packages                          
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/main Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/restricted Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/universe Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/universe Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/multiverse Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [7487B]
Get:8 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/restricted Packages [8001B]
Get:9 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/main Packages [421kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [120kB]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [11.3kB]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [54.3kB]   
Get:13 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/multiverse Packages [27.7kB]
Get:14 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy-updates/universe Packages [163kB]   
Fetched 930kB in 36s (25.2kB/s)                                               
Reading package lists... Done


[   15.280552] Calibrating delay using timer specific routine.. 3602.37 BogoMIPS (lpj=7204759)
[   15.280579] Security Framework initialized
[   15.280585] SELinux:  Disabled at boot.
[   15.280601] AppArmor: AppArmor initialized
[   15.280604] Failure registering capabilities with primary security module.
[   15.280612] Mount-cache hash table entries: 512
[   15.280722] Initializing cgroup subsys ns
[   15.280726] Initializing cgroup subsys cpuacct
[   15.280735] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001 00000000
[   15.280743] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   15.280746] CPU: L2 Cache: 256K (64 bytes/line)
[   15.280749] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00020410 00000001 00000000 00000001 00000000
[   15.280758] Compat vDSO mapped to ffffe000.
[   15.280769] Checking 'hlt' instruction... OK.
[   15.296793] SMP alternatives: switching to UP code
[   15.297856] Freeing SMP alternatives: 11k freed
[   15.297970] Early unpacking initramfs... done
[   15.638676] ACPI: Core revision 20070126
[   15.638752] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.642422] CPU0: AMD Sempron(tm) Processor 2800+ stepping 02
[   15.642435] Total of 1 processors activated (3602.37 BogoMIPS).
[   15.642546] ENABLING IO-APIC IRQs
[   15.642713] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[   15.787841] Brought up 1 CPUs
[   15.787863] CPU0 attaching sched-domain:
[   15.787866]  domain 0: span 01
[   15.787868]   groups: 01
[   15.788020] net_namespace: 64 bytes
[   15.788027] Booting paravirtualized kernel on bare hardware
[   15.788469] Time: 23:15:15  Date: 02/10/09
[   15.788492] NET: Registered protocol family 16
[   15.788654] EISA bus registered
[   15.788680] ACPI: bus type pci registered
[   15.793359] PCI: PCI BIOS revision 3.00 entry at 0xf1f20, last bus=5
[   15.793361] PCI: Using configuration type 1
[   15.793370] Setting up standard PCI resources
[   15.798036] ACPI: EC: Look up EC in DSDT
[   15.804705] ACPI: Interpreter enabled
[   15.804708] ACPI: (supports S0 S1 S3 S4 S5)
[   15.804721] ACPI: Using IOAPIC for interrupt routing
[   15.814231] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.814779] PCI: Transparent bridge - 0000:00:09.0
[   15.815027] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.815335] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[   15.885776] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   15.885960] ACPI: PCI Interrupt Link [LNK2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   15.886140] ACPI: PCI Interrupt Link [LNK3] (IRQs *3 4 5 7 9 10 11 12 14 15)
[   15.886323] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   15.886502] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   15.886683] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   15.886862] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   15.887043] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   15.887223] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   15.887402] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   15.887582] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   15.887768] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   15.887947] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   15.888135] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[   15.888324] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   15.888511] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[   15.888714] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[   15.888907] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[   15.889099] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[   15.889290] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[   15.889420] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   15.889619] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[   15.889816] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[   15.890013] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[   15.890210] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[   15.890406] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[   15.890603] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[   15.890799] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[   15.890996] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[   15.891200] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[   15.891407] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[   15.891610] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[   15.891754] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.891781] pnp: PnP ACPI init
[   15.891788] ACPI: bus type pnp registered
[   15.897190] pnpacpi: exceeded the max number of mem resources: 12
[   15.897250] pnp: PnP ACPI: found 16 devices
[   15.897252] ACPI: ACPI bus type pnp unregistered
[   15.897256] PnPBIOS: Disabled by ACPI PNP
[   15.897444] PCI: Using ACPI for IRQ routing
[   15.897449] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   15.975549] NET: Registered protocol family 8
[   15.975551] NET: Registered protocol family 20
[   15.975607] AppArmor: AppArmor Filesystem Enabled
[   15.979511] Time: tsc clocksource has been installed.
[   15.987531] system 00:01: ioport range 0x4000-0x407f has been reserved
[   15.987534] system 00:01: ioport range 0x4080-0x40ff has been reserved
[   15.987537] system 00:01: ioport range 0x4400-0x447f has been reserved
[   15.987540] system 00:01: ioport range 0x4480-0x44ff has been reserved
[   15.987542] system 00:01: ioport range 0x4800-0x487f has been reserved
[   15.987545] system 00:01: ioport range 0x4880-0x48ff has been reserved
[   15.987551] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   15.987554] system 00:02: ioport range 0x800-0x87f has been reserved
[   15.987557] system 00:02: ioport range 0x290-0x297 has been reserved
[   15.987569] system 00:0e: iomem range 0xe0000000-0xefffffff could not be reserved
[   15.987575] system 00:0f: iomem range 0xf0000-0xf3fff could not be reserved
[   15.987578] system 00:0f: iomem range 0xf4000-0xf7fff could not be reserved
[   15.987580] system 00:0f: iomem range 0xf8000-0xfbfff could not be reserved
[   15.987583] system 00:0f: iomem range 0xfc000-0xfffff could not be reserved
[   15.987586] system 00:0f: iomem range 0x7fff0000-0x7fffffff could not be reserved
[   15.987589] system 00:0f: iomem range 0xffff0000-0xffffffff could not be reserved
[   15.987592] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   15.987595] system 00:0f: iomem range 0x100000-0x7ffeffff could not be reserved
[   15.987598] system 00:0f: iomem range 0xfec00000-0xfec00fff could not be reserved
[   15.987601] system 00:0f: iomem range 0xfee00000-0xfeefffff could not be reserved
[   15.987604] system 00:0f: iomem range 0xfefff000-0xfeffffff could not be reserved
[   15.987607] system 00:0f: iomem range 0xfff80000-0xfff80fff has been reserved
[   16.017920] PCI: Bridge: 0000:00:09.0
[   16.017922]   IO window: a000-afff
[   16.017925]   MEM window: d3000000-d30fffff
[   16.017927]   PREFETCH window: disabled.
[   16.017930] PCI: Bridge: 0000:00:0b.0
[   16.017931]   IO window: disabled.
[   16.017933]   MEM window: disabled.
[   16.017935]   PREFETCH window: disabled.
[   16.017938] PCI: Bridge: 0000:00:0c.0
[   16.017939]   IO window: disabled.
[   16.017941]   MEM window: disabled.
[   16.017943]   PREFETCH window: disabled.
[   16.017946] PCI: Bridge: 0000:00:0d.0
[   16.017947]   IO window: disabled.
[   16.017949]   MEM window: disabled.
[   16.017951]   PREFETCH window: disabled.
[   16.017954] PCI: Bridge: 0000:00:0e.0
[   16.017955]   IO window: disabled.
[   16.017957]   MEM window: d0000000-d2ffffff
[   16.017960]   PREFETCH window: c0000000-cfffffff
[   16.017967] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   16.017978] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   16.017985] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   16.017991] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   16.017997] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   16.018007] NET: Registered protocol family 2
[   16.055464] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.055745] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.056559] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.056963] TCP: Hash tables configured (established 131072 bind 65536)
[   16.056967] TCP reno registered
[   16.067503] checking if image is initramfs... it is
[   16.518698] Switched to high resolution mode on CPU 0
[   16.720324] Freeing initrd memory: 7326k freed
[   16.720853] audit: initializing netlink socket (disabled)
[   16.720864] audit(1234307715.420:1): initialized
[   16.721017] highmem bounce pool size: 64 pages
[   16.722587] VFS: Disk quotas dquot_6.5.1
[   16.722652] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.722776] io scheduler noop registered
[   16.722778] io scheduler anticipatory registered
[   16.722780] io scheduler deadline registered
[   16.722789] io scheduler cfq registered (default)
[   16.722806] pci 0000:00:00.0: Enabling HT MSI Mapping
[   16.738344] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   16.738351] PCI: Found enabled HT MSI Mapping on 0000:00:0b.0
[   16.738360] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   16.738366] PCI: Found enabled HT MSI Mapping on 0000:00:0c.0
[   16.738374] pci 0000:00:0d.0: Enabling HT MSI Mapping
[   16.738381] PCI: Found enabled HT MSI Mapping on 0000:00:0d.0
[   16.738389] pci 0000:00:0e.0: Enabling HT MSI Mapping
[   16.738395] PCI: Found enabled HT MSI Mapping on 0000:00:0e.0
[   16.738420] Boot video device is 0000:01:00.0
[   16.738512] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   16.738532] assign_interrupt_mode Found MSI capability
[   16.738550] Allocate Port Service[0000:00:0b.0:pcie00]
[   16.738605] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   16.738624] assign_interrupt_mode Found MSI capability
[   16.738637] Allocate Port Service[0000:00:0c.0:pcie00]
[   16.738691] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   16.738710] assign_interrupt_mode Found MSI capability
[   16.738723] Allocate Port Service[0000:00:0d.0:pcie00]
[   16.738776] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   16.738794] assign_interrupt_mode Found MSI capability
[   16.738806] Allocate Port Service[0000:00:0e.0:pcie00]
[   16.738988] isapnp: Scanning for PnP cards...
[   17.091122] isapnp: No Plug & Play device found
[   17.115577] Real Time Clock Driver v1.12ac
[   17.115667] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.115767] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.116281] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   17.116944] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.117002] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.117087] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.119912] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.119916] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.129729] mice: PS/2 mouse device common for all mice
[   17.129827] EISA: Probing bus 0 at eisa.0
[   17.129839] Cannot allocate resource for EISA slot 4
[   17.129851] EISA: Detected 0 cards.
[   17.129853] cpuidle: using governor ladder
[   17.129855] cpuidle: using governor menu
[   17.129934] NET: Registered protocol family 1
[   17.129957] Using IPI No-Shortcut mode
[   17.129985] registered taskstats version 1
[   17.130093]   Magic number: 13:884:301
[   17.130095]   hash matches /build/buildd/linux-2.6.24/drivers/base/power/main.c:107
[   17.130196]   hash matches device tty30
[   17.130230] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.130232] EDD information not available.
[   17.130445] Freeing unused kernel memory: 368k freed
[   17.157651] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.399774] fuse init (API version 7.9)
[   18.418044] ACPI: Fan [FAN] (on)
[   18.425125] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.426702] ACPI: Thermal Zone [THRM] (40 C)
[   19.376911] usbcore: registered new interface driver usbfs
[   19.376932] usbcore: registered new interface driver hub
[   19.394128] usbcore: registered new device driver usb
[   19.410586] SCSI subsystem initialized
[   19.418082] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   19.418447] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 23
[   19.418454] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 23 (level, low) -> IRQ 16
[   19.418465] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   19.418468] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   19.418688] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[   19.418701] ohci_hcd 0000:00:02.0: irq 16, io mem 0xd3104000
[   19.476080] usb usb1: configuration #1 chosen from 1 choice
[   19.476102] hub 1-0:1.0: USB hub found
[   19.476109] hub 1-0:1.0: 10 ports detected
[   19.481333] libata version 3.00 loaded.
[   19.578154] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   19.578162] ACPI: PCI Interrupt 0000:05:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 17
[   19.578173] ohci_hcd 0000:05:08.0: OHCI Host Controller
[   19.578195] ohci_hcd 0000:05:08.0: new USB bus registered, assigned bus number 2
[   19.578208] ohci_hcd 0000:05:08.0: irq 17, io mem 0xd3010000
[   19.578515] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[   19.578518] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] -> GSI 22 (level, low) -> IRQ 18
[   19.578525] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   19.578528] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   19.578546] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 3
[   19.578571] ehci_hcd 0000:00:02.1: debug port 1
[   19.578574] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   19.578580] ehci_hcd 0000:00:02.1: irq 18, io mem 0xd3105000
[   19.589808] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.589920] usb usb3: configuration #1 chosen from 1 choice
[   19.589943] hub 3-0:1.0: USB hub found
[   19.589951] hub 3-0:1.0: 10 ports detected
[   19.693775] usb usb2: configuration #1 chosen from 1 choice
[   19.693797] hub 2-0:1.0: USB hub found
[   19.693804] hub 2-0:1.0: 3 ports detected
[   19.772080] Floppy drive(s): fd0 is 1.44M
[   19.789315] FDC 0 is a post-1991 82077
[   19.797821] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   19.797829] ACPI: PCI Interrupt 0000:05:08.1[B] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 19
[   19.797841] ohci_hcd 0000:05:08.1: OHCI Host Controller
[   19.797863] ohci_hcd 0000:05:08.1: new USB bus registered, assigned bus number 4
[   19.797876] ohci_hcd 0000:05:08.1: irq 19, io mem 0xd3011000
[   19.883211] usb usb4: configuration #1 chosen from 1 choice
[   19.883237] hub 4-0:1.0: USB hub found
[   19.883244] hub 4-0:1.0: 2 ports detected
[   19.985658] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   19.985666] ACPI: PCI Interrupt 0000:05:08.2[C] -> Link [APC1] -> GSI 16 (level, low) -> IRQ 20
[   19.985677] ehci_hcd 0000:05:08.2: EHCI Host Controller
[   19.985707] ehci_hcd 0000:05:08.2: new USB bus registered, assigned bus number 5
[   19.985747] ehci_hcd 0000:05:08.2: irq 20, io mem 0xd3012000
[   19.997150] ehci_hcd 0000:05:08.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.997260] usb usb5: configuration #1 chosen from 1 choice
[   19.997282] hub 5-0:1.0: USB hub found
[   19.997288] hub 5-0:1.0: 5 ports detected
[   20.101199] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   20.101536] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[   20.101542] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] -> GSI 21 (level, low) -> IRQ 21
[   20.101548] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   20.520327] usb 3-4: new high speed USB device using ehci_hcd and address 3
[   20.620519] forcedeth 0000:00:0a.0: ifname eth0, PHY OUI 0x1374 @ 0, addr 00:17:31:16:87:81
[   20.620524] forcedeth 0000:00:0a.0: highdma csum timirq gbit lnktim desc-v3
[   20.624484] pata_amd 0000:00:06.0: version 0.3.10
[   20.624535] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   20.628656] scsi0 : pata_amd
[   20.631580] scsi1 : pata_amd
[   20.632395] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[   20.632398] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[   20.654256] usb 3-4: configuration #1 chosen from 1 choice
[   20.655200] hub 3-4:1.0: USB hub found
[   20.655551] hub 3-4:1.0: 4 ports detected
[   20.804198] ata1.00: ATA-6: WDC WD800BB-63JKC0, 05.01C05, max UDMA/100
[   20.804202] ata1.00: 156301488 sectors, multi 1: LBA48 
[   20.811948] ata1.01: ATA-7: WDC WD5000AAKB-00UKA0, 07.01N01, max UDMA/100
[   20.811951] ata1.01: 976773168 sectors, multi 1: LBA48 
[   20.820095] ata1.00: configured for UDMA/100
[   20.836212] ata1.01: configured for UDMA/100
[   21.127338] usb 5-4: new high speed USB device using ehci_hcd and address 2
[   21.271894] usb 5-4: configuration #1 chosen from 1 choice
[   21.518957] ata2.00: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[   21.518978] ata2.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[   21.518990] ata2.00: limited to UDMA/33 due to 40-wire cable
[   21.518992] ata2.01: limited to UDMA/33 due to 40-wire cable
[   21.574633] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   21.706600] ata2.00: configured for UDMA/33
[   21.807438] usb 1-3: configuration #1 chosen from 1 choice
[   21.894299] ata2.01: configured for UDMA/33
[   21.894399] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-63JK 05.0 PQ: 0 ANSI: 5
[   21.894787] scsi 0:0:1:0: Direct-Access     ATA      WDC WD5000AAKB-0 07.0 PQ: 0 ANSI: 5
[   21.895836] scsi 1:0:0:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[   21.896862] scsi 1:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[   21.899584] sata_nv 0000:00:07.0: version 3.5
[   21.899988] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[   21.899995] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] -> GSI 20 (level, low) -> IRQ 22
[   21.899999] sata_nv 0000:00:07.0: Using ADMA mode
[   21.900037] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   21.901914] scsi2 : sata_nv
[   21.902246] scsi3 : sata_nv
[   21.902418] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xd800 irq 22
[   21.902421] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xd808 irq 22
[   22.010196] usb 3-4.1: new high speed USB device using ehci_hcd and address 4
[   22.104133] usb 3-4.1: configuration #1 chosen from 1 choice
[   22.105096] hub 3-4.1:1.0: USB hub found
[   22.105433] hub 3-4.1:1.0: 4 ports detected
[   22.212518] usbcore: registered new interface driver libusual
[   22.216844] ata3: SATA link down (SStatus 0 SControl 300)
[   22.217867] Initializing USB Mass Storage driver...
[   22.219196] scsi4 : SCSI emulation for USB Mass Storage devices
[   22.220103] usbcore: registered new interface driver usb-storage
[   22.220109] USB Mass Storage support registered.
[   22.220199] usb-storage: device found at 2
[   22.220201] usb-storage: waiting for device to settle before scanning
[   22.525120] ata4: SATA link down (SStatus 0 SControl 300)
[   22.525560] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 23
[   22.525563] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] -> GSI 23 (level, low) -> IRQ 16
[   22.525568] sata_nv 0000:00:08.0: Using ADMA mode
[   22.525607] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   22.525702] scsi5 : sata_nv
[   22.525987] scsi6 : sata_nv
[   22.526151] ata5: SATA max UDMA/133 cmd 0x9e0 ctl 0xbe0 bmdma 0xc400 irq 16
[   22.526154] ata6: SATA max UDMA/133 cmd 0x960 ctl 0xb60 bmdma 0xc408 irq 16
[   22.836626] ata5: SATA link down (SStatus 0 SControl 300)
[   23.148131] ata6: SATA link down (SStatus 0 SControl 300)
[   23.162445] Driver 'sd' needs updating - please use bus_type methods
[   23.162521] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.162532] sd 0:0:0:0: [sda] Write Protect is off
[   23.162535] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.162549] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.162587] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   23.162595] sd 0:0:0:0: [sda] Write Protect is off
[   23.162598] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   23.162610] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.162614]  sda: sda1 sda2 <<4>Driver 'sr' needs updating - please use bus_type methods
[   23.188137]  sda5 sda6 >
[   23.198431] sd 0:0:0:0: [sda] Attached SCSI disk
[   23.198482] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   23.198493] sd 0:0:1:0: [sdb] Write Protect is off
[   23.198495] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.198510] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.198546] sd 0:0:1:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   23.198554] sd 0:0:1:0: [sdb] Write Protect is off
[   23.198556] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[   23.198570] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   23.198573]  sdb: sdb1 sdb2 sdb3 sdb4 < sdb5 >
[   23.227333] sd 0:0:1:0: [sdb] Attached SCSI disk
[   23.237200] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   23.237218] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   23.237234] sr 1:0:0:0: Attached scsi generic sg2 type 5
[   23.237248] scsi 1:0:1:0: Attached scsi generic sg3 type 5
[   23.241650] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.241656] Uniform CD-ROM driver Revision: 3.20
[   23.241704] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   23.249612] sr1: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   23.249663] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   23.904212] Attempting manual resume
[   23.904216] swsusp: Resume From Partition 8:5
[   23.904218] PM: Checking swsusp image.
[   23.904406] PM: Resume from disk failed.
[   23.926254] kjournald starting.  Commit interval 5 seconds
[   23.926268] EXT3-fs: mounted filesystem with ordered data mode.
[   27.210206] usb-storage: device scan complete
[   27.211193] scsi 4:0:0:0: Direct-Access     Generic  STORAGE DEVICE   9451 PQ: 0 ANSI: 0
[   27.212458] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[   27.212487] sd 4:0:0:0: Attached scsi generic sg4 type 0
[   33.429640] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.467833] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.667530] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   33.667546] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   33.923198] input: Power Button (FF) as /devices/virtual/input/input2
[   33.953519] ACPI: Power Button (FF) [PWRF]
[   33.953606] input: Power Button (CM) as /devices/virtual/input/input3
[   33.966988] ACPI: Power Button (CM) [PWRB]
[   34.513095] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
[   34.693910] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   34.837943] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   34.837951] ACPI: PCI Interrupt 0000:05:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 23
[   36.754961] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   36.754967] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] -> GSI 22 (level, low) -> IRQ 18
[   36.754988] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   36.826652] ttySHSF0 at I/O 0xa000 (irq = 23) is a Conexant HSF softmodem (PCI-127a:2016-122d:4056)
[   37.078046] intel8x0_measure_ac97_clock: measured 54726 usecs
[   37.078050] intel8x0: clocking to 46908
[   37.793550] Linux agpgart interface v0.102
[   38.398146] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   38.410661] parport_pc 00:09: reported by Plug and Play ACPI
[   38.410708] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   39.042941] Bluetooth: Core ver 2.11
[   39.070934] NET: Registered protocol family 31
[   39.070937] Bluetooth: HCI device and connection manager initialized
[   39.070942] Bluetooth: HCI socket layer initialized
[   39.128159] Bluetooth: HCI USB driver ver 2.9
[   39.130378] usbcore: registered new interface driver hci_usb
[   39.292897] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 17
[   39.292906] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   39.293121] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   41.685316] lp0: using parport0 (interrupt-driven).
[   41.761427] Adding 4088500k swap on /dev/sda5.  Priority:-1 extents:1 across:4088500k
[  122.688769] EXT3 FS on sda1, internal journal
[  123.371398] kjournald starting.  Commit interval 5 seconds
[  123.371637] EXT3 FS on sda6, internal journal
[  123.371641] EXT3-fs: mounted filesystem with ordered data mode.
[  124.761766] ip_tables: (C) 2000-2006 Netfilter Core Team
[  126.333890] No dock devices found.
[  126.773663] powernow-k8: Power state transitions not supported
[  126.813508] ACPI Exception (processor_perflib-0234): AE_NOT_FOUND, Evaluating _PSS [20070126]
[  127.818127] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  127.818132] apm: overridden by ACPI.
[  147.731925] Bluetooth: L2CAP ver 2.9
[  147.731930] Bluetooth: L2CAP socket layer initialized
[  147.776884] Bluetooth: RFCOMM socket layer initialized
[  147.777185] Bluetooth: RFCOMM TTY layer initialized
[  147.777188] Bluetooth: RFCOMM ver 1.8
[  152.531749] [7198]: VMCI: Driver initialized.
[  152.532063] [7198]: Module vmmon: registered with major=10 minor=165
[  152.532384] [7198]: Module vmmon: initialized
[  152.592246] /dev/vmnet: open called by PID 7219 (vmnet-bridge)
[  152.592259] /dev/vmnet: hub 0 does not exist, allocating memory.
[  152.592269] /dev/vmnet: port on hub 0 successfully opened
[  152.592285] bridge-eth0: enabling the bridge
[  152.592289] bridge-eth0: up
[  152.592290] bridge-eth0: already up
[  152.592293] bridge-eth0: attached
[  152.655870] /dev/vmnet: open called by PID 7233 (vmnet-natd)
[  152.655881] /dev/vmnet: hub 8 does not exist, allocating memory.
[  152.655893] /dev/vmnet: port on hub 8 successfully opened
[  162.609689] /dev/vmnet: open called by PID 7651 (vmnet-netifup)
[  162.609704] /dev/vmnet: hub 1 does not exist, allocating memory.
[  162.609715] /dev/vmnet: port on hub 1 successfully opened



I have the feeling that the "dmesg" output is longer but it's cut from the top - this is all that comes.

However T-Bird appears to work again?? 

I will download and install updates, maybe that'll fix things (i HATE updates).

Kind regards.....

Thanh

---

### Post by pytheas22 on 2009-02-10
It actually looks like things should be working now.  apt-get (the backend to Synaptic) works, and so does pinging.  Let me know if it breaks again.

---

### Post by Thanh-BKK on 2009-02-10
Hi. 

Yeah i am downloading (via update manager) 277 updates including a kernel..... there are two possibilities, either it will screw up big time or it will work after that. I normally try to prevent updates at all cost once the system runs because updates regularly break previously working things..... however right now i HAVE a problem and it might get fixed.

The power failure happened yesterday, when i came home from work the computer was off. So i started it and it started normally, also all apps were working. I then tested the UPS (button on the front) and the computer shut off, so i know the UPS is toast, probably the battery. However i restarted the computer and again it started normally, i then only shut it down and went to sleep. During that shutdown it got "stuck" for a bit and brought up those network-manager-related error text bits that so many people encountered (including me right after installing Ubuntu for the first time). 

And then in the morning today, Firefox would work fine but neither T-Bird (time out), uTorrent (under Wine, also time out) or Synaptic (again time out). 

I don't think it's an issue with my router or the ADSL as Firefox worked fine?? If something is wrong with the ADSL usually torrents keep going but web sites time out. 

Anyway i'll see what happens after the updates, if all fails i got a second Ubuntu-box so i can still post here :)

Kind regards.....

Thanh

---

### Post by Thanh-BKK on 2009-02-10
Hello again.

I'm back on, new kernel and all, everything appears to be working fine. However now i get a bunch of text on the screen during startup AND shutdown. It starts normally (splash screen) but at about 80% the splash screen disappears and a terminal-like screen appears with lots of text running (on startup), followed by the brown-ish solid colour screen which comes immediately before the desktop.

On shutdown again it starts to shut down normally (splash screen), at roughly 80% this disappears to give me the terminal-like screen again with only a cursor blinking on top left corner. After some time (25 seconds roughly) the network manager related error lines come up, then the splash screen appears for a second or so and the machine turns off normally.

I have already tried the "login screen - edit command" trick which fixed this problem initially but this time it doesn't work.

Any idea how to fix that, or should i open a new topic for that?

Kind regards......

Thanh

---

### Post by pytheas22 on 2009-02-11
What are the error messages that you're getting?  Can you post here at least a part of the exact phrase?

Some of the messages that Network Manager spams to standard output are not necessarily indicative of any serious problem; there could be various other causes.

Also, have you tried shutting down and rebooting two or three times, with the same behavior repeated each time?

---

### Post by Thanh-BKK on 2009-02-11
Hello.

Thanks for offering to help. I get the well-known lines of text that everybody sems to have gotten at some stage....

NetworkManager: <WARN> nm_signal_handler(): Caught signal 15, shutting down normally.
NetworkManager: <INFO> Caught termination signal
NetworkManager: <DEBUG> [1209404787.824467] nm_print_open_socks(): Open Sockets List:
NetworkManager: <DEBUG> [1209404787.824467] nm_print_open_socks(): Open Sockets List Done.
NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed
NetworkManager: <WARN> nm_dbus_init(): nm_dbus_init() could not get the system bus. Make sure the message bus daemon is running!

This was a copy-paste from another forum post about the same issue, as i am currently at work and on a Windows-bnox. However "my" errors are like this, i used to have that problem some time ago after fresh installing Ubuntu. A "fix" was this: 

1. Go to System - Administration - Login Window.

2. Under 'General', press "Edit commands ...'

3. Select 'Halt command' - in 'Path' box, cut the text in quotes (I.e. "Shut down via gdm") - press "Apply command change" - paste the text back - press 'Apply command change'

4. Select 'Reboot command' and do as for 3. above

Which helped previously, the error messages never showed up again. However since those power failures yesterday it's back, and that mentioned trick doesn't help anymore. And updating (including a new kernel) didn't solve it, either. 

The stuff that appears during startup only takes a couple of seconds so it's not an issue - but this one during shutdown delays the shutdown process, it now takes about twice as long as usual.

Kind regards.....

Thanh

PS i already re-installed the "usplash" and "usplash-theme-ubuntu" and that didn't help either, and yes, i did reboot or shut down and cold boot a number of times, nothing changed.

---

### Post by pytheas22 on 2009-02-11
I think there are several possible causes for this issue.  You might want to take a look at this [bug report]("https://answers.launchpad.net/ubuntu/+question/16914"), where there are a few solutions (including the one you already tried, but in addition to others), like editing your grub boot options.  Does any of them help?

---

