---
title: "Help Me Please =]"
date: 2009-06-14
forum: General Help
---

### Post by The Real Dave on 2009-06-14
Ok, for a while now, I've been thinking about upgrading my CPU. 

I currently have a 2.93 Ghz Pentium IV chip (**_[this]("http://www.geeks.com/details.asp?invtid=P42930E775-N&cat=CPU")_** model I think)

```
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: CPU 1
          size: 2926MHz
          capacity: 2926MHz
          width: 64 bits
          clock: 532MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
```

I'm thinking about upgrading to a 2.5Ghz _**[Pentium Dual Core ]("http://www.amazon.co.uk/gp/product/B001ENB1FA/ref=s9_simz_gw_s3_p23_t1?pf_rd_m=A3P5ROKL5A1OLE&pf_rd_s=center-1&pf_rd_r=1AY8B7MC6B10DYSQPFZZ&pf_rd_t=101&pf_rd_p=467198433&pf_rd_i=468294")**_

My motherboard says that FSB is 800Mhz, but my current CPU is 532Mhz as far as I can tell. Also, your RAM speed can affect what CPU's you can use ya? I have 512+1024Mb of **_[PC-4200 RAM]("http://www.memoryc.com/computermemory/ddr2ram/1gbadata533pc24200.html")_** 

Will this CPU be compatible with the rest of my computer? 

Output of "sudo lshw"

```
dave@ubuntu:~$ sudo lshw
ubuntu                    
    description: Desktop Computer
    product: Aspire T650/E500/AP F5
    vendor: ACER
    version: To Be Filled By O.E.M.
    serial: &#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: ERC410M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
       vendor: ACER
       physical id: 0
       version: To be filled by O.E.M.
       serial: To be filled by O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: R01-E4 (09/21/2005)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 2.93GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 15.4.1
          serial: 0000-0F41-0000-0000-0000-0000
          slot: CPU 1
          size: 2926MHz
          capacity: 2926MHz
          width: 64 bits
          clock: 532MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc up pebs bts pni dtes64 monitor ds_cpl tm2 cid cx16 xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 16KiB
             capacity: 16KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory
          description: System Memory
          physical id: 29
          slot: System board or motherboard
          size: 1536MiB
        *-bank:0
             description: DIMM [empty]
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
        *-bank:1
             description: DIMM [empty]
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
        *-bank:2
             description: DIMM DDR Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 512MiB
             width: 64 bits
        *-bank:3
             description: DIMM DDR Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits
     *-pci
          description: Host bridge
          product: Radeon Xpress 200 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 64 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master cap_list
           *-display UNCLAIMED
                description: VGA compatible controller
                product: RC410 [Radeon Xpress 200]
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=64 mingnt=8
        *-pci:1
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ALi Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci ht bus_master cap_list
           *-communication UNCLAIMED
                description: Communication controller
                product: V.92 56K WinModem
                vendor: Agere Systems
                physical id: 12
                bus info: pci@0000:02:12.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=14 mingnt=252
           *-network
                description: Ethernet interface
                product: 88E8001 Gigabit Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 15
                bus info: pci@0000:02:15.0
                logical name: eth0
                version: 13
                serial: 00:14:2a:6b:15:35
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.1 latency=64 link=yes maxlatency=31 mingnt=23 module=skge multicast=yes port=twisted pair speed=100MB/s
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306 Fire II IEEE 1394 OHCI Link Layer Controller
                vendor: VIA Technologies, Inc.
                physical id: 16
                bus info: pci@0000:02:16.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=32 module=ohci1394
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 maxlatency=80
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 maxlatency=32 mingnt=16 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: High Definition Audio/AC'97 Host Controller
             vendor: ALi Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 00
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=64 maxlatency=80 mingnt=16 module=snd_hda_intel
        *-isa
             description: ISA bridge
             product: PCI to LPC Controller
             vendor: ALi Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 31
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0 maxlatency=24 mingnt=1
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 1e.1
             bus info: pci@0000:00:1e.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             logical name: scsi4
             version: c7
             width: 32 bits
             clock: 66MHz
             capabilities: ide pm bus_master cap_list emulated
             configuration: driver=pata_ali latency=32 module=pata_ali
           *-cdrom:0
                description: DVD-RAM writer
                physical id: 0.0.0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom1
                logical name: /dev/cdrw1
                logical name: /dev/dvd1
                logical name: /dev/dvdrw1
                logical name: /dev/scd0
                logical name: /dev/sr0
                capabilities: audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: status=nodisc
           *-cdrom:1
                description: DVD reader
                product: DVD-ROM DVD-114
                vendor: Compaq
                physical id: 0.1.0
                bus info: scsi@4:0.1.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd1
                logical name: /dev/sr1
                logical name: /media/MAFIA_CD_1
                version: 1.14
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/MAFIA_CD_1
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,uid=1000,utf8 state=mounted
        *-storage
             description: RAID bus controller
             product: ULi 5287 SATA
             vendor: ALi Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             logical name: scsi0
             logical name: scsi1
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=sata_uli latency=128
           *-disk:0
                description: ATA Disk
                product: HDS728080PLA380
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: PF2O
                serial: PFDB20S5SNAJLK
                size: 76GiB (82GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=67df67df
              *-volume:0
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: FAT32
                   serial: 4a06-cad8
                   size: 57GiB
                   capacity: 57GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 729f53f0-4804-7444-ada2-8ac4f8455c48
                   size: 19GiB
                   capacity: 19GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2009-06-13 08:00:30 filesystem=ntfs state=clean
           *-disk:1
                description: ATA Disk
                product: SAMSUNG HD322HJ
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/sdb
                version: 1AC0
                serial: S17AJ9AQB23497
                size: 298GiB (320GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0009628c
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: /dev/sdb1
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux swap / Solaris partition
                      physical id: 5
                      logical name: /dev/sdb5
                      capacity: 996MiB
                      capabilities: nofs
                 *-logicalvolume:1
                      description: Linux filesystem partition
                      physical id: 6
                      logical name: /dev/sdb6
                      logical name: /
                      capacity: 37GiB
                      capabilities: bootable
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sdb7
                      capacity: 10197MiB
              *-volume:1
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 2
                   bus info: scsi@1:0.0.0,2
                   logical name: /dev/sdb2
                   version: FAT32
                   serial: 80e4-c892
                   size: 48GiB
                   capacity: 48GiB
                   capabilities: primary bootable fat initialized
                   configuration: FATs=2 filesystem=fat label=WINDOWS XP
              *-volume:2
                   description: Windows FAT volume
                   vendor: MSWIN4.1
                   physical id: 3
                   bus info: scsi@1:0.0.0,3
                   logical name: /dev/sdb3
                   logical name: /media/Data
                   version: FAT32
                   serial: 4a00-88fe
                   size: 200GiB
                   capacity: 200GiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
     *-scsi
          physical id: 1
          bus info: usb@4:2
          logical name: scsi6
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk:0
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@6:0.0.0
             logical name: /dev/sdc
        *-disk:1
             description: SCSI Disk
             physical id: 0.0.1
             bus info: scsi@6:0.0.1
             logical name: /dev/sdd
        *-disk:2
             description: SCSI Disk
             physical id: 0.0.2
             bus info: scsi@6:0.0.2
             logical name: /dev/sde
        *-disk:3
             description: SCSI Disk
             physical id: 0.0.3
             bus info: scsi@6:0.0.3
             logical name: /dev/sdf
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6e:06:ce:e6:61:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

I've never messed around with Processors before, so advice is extremely and gratefully wanted :D:D


**EDIT**: Just one more thing, would [**_this_**]("http://www.amazon.co.uk/exec/obidos/ASIN/B000KB96QS/ref=ord_cart_shr?_encoding=UTF8&m=A17AS5ETPMZ9A1") cooler be enough to keep the new CPU cool?

---

### Post by overdrank on 2009-06-14
Moved to General Help :)

---

### Post by Therion on 2009-06-14
Your processor of choice will fit your motherboard, yes: They're both LGA775.

RAM speed has nothing to do with processor speed.  The motherboard determines what RAM you can use.

The HSF (heat-sink fan) choice is a good one.  Yes, it's compatible etc.

In short, you're good to go but...  Put some thermal paste on your shopping list; that's the only other thing I can think of that you'll need.

---

### Post by Yellow Pasque on 2009-06-14
> Your processor of choice will fit your motherboard, yes: They're both LGA775.
Unfortunately, that doesn't necessarily mean it's compatible. Most older Socket 775 motherboards don't have the proper VRD to support Core 2 chips. Make sure yours is compatible before buying a new CPU.

If in doubt, post your mobo model (use info from dmidecode command if unsure). Also, look at the BIOS updates for your motherboard and see if any mention support for Core/2.

---

### Post by The Real Dave on 2009-06-14
Thanks for the quick response :D

Ok, here's the output of "sudo dmidecode"

```
# dmidecode 2.9
SMBIOS 2.3 present.
53 structures occupying 1908 bytes.
Table at 0x000FBE50.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: R01-E4 
	Release Date: 09/21/2005
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer: ACER
	Product Name: Aspire T650/E500/AP F5
	Version: To Be Filled By O.E.M.
	Serial Number: ......................
	UUID: 00020003-0004-0005-0006-000700080009
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: ACER
	Product Name: ERC410M...............
	Version: To be filled by O.E.M.
	Serial Number: To be filled by O.E.M.

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: ACER
	Type: Desktop
	Lock: Not Present
	Version: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: Asset tag number:at least 22 digits
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Xeon MP
	Manufacturer: Intel            
	ID: 41 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 4, Stepping 1
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) 4 CPU 2.93GHz                   
	Voltage: 3.3 V 2.9 V
	External Clock: 532 MHz
	Max Speed: 2926 MHz
	Current Speed: 2926 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 16 KB
	Maximum Size: 16 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Pipeline Burst
	Installed SRAM Type: Pipeline Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Internal
	Installed Size: 0 KB
	Maximum Size: 0 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 4096 MB
	Maximum Total Memory Size: 16384 MB
	Supported Speeds:
		Unknown
	Supported Memory Types:
		DIMM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 4
		0x0009
		0x000A
		0x000B
		0x000C
	Enabled Error Correcting Capabilities:
		None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 0
	Current Speed: Unknown
	Type: DIMM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 0
	Current Speed: Unknown
	Type: DIMM
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM2
	Bank Connections: 0
	Current Speed: Unknown
	Type: DIMM
	Installed Size: 512 MB (Single-bank Connection)
	Enabled Size: 512 MB (Single-bank Connection)
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM5
	Bank Connections: 0
	Current Speed: Unknown
	Type: DIMM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4A1
	Internal Connector Type: None
	External Reference Designator: LPT 1
	External Connector Type: DB-25 male
	Port Type: Parallel Port ECP/EPP

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: COM A
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B1 - AUX IN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B2 - CDIN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J2 - PRI IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J1 - SEC IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4J1 - FLOPPY
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H1 - FRONT PNL
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1B1 - CHASSIS REAR FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2F1 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8B4 - FRONT FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G2 - FNT USB
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6C3 - FP AUD
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G1 - CONFIG
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8C1 - SCSI LED
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9J2 - INTRUDER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G4 - ITP
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2H1 - MAIN POWER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0025, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP
	Type: 32-bit AGP 4x
	Current Usage: In Use
	Length: Short
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0026, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0027, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:   To Be Filled By O.E.M.

Handle 0x0028, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 1 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x002A, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x160000003FF
	Range Size: 1476395009 kB
	Physical Array Handle: 0x0029
	Partition Width: 0

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x002C, DMI type 126, 19 bytes
Inactive

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: Unknown
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x002E, DMI type 126, 19 bytes
Inactive

Handle 0x002F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: DDR
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x0030, DMI type 126, 19 bytes
Inactive

Handle 0x0031, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK3
	Type: DDR
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: PartNum3

Handle 0x0032, DMI type 126, 19 bytes
Inactive

Handle 0x0033, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0034, DMI type 127, 4 bytes
End Of Table


```

Unfortunately it doesn't seem to say my motherboard model number :confused:

I did find [_**this**_]("http://members.driverguide.com/driver/detail.php?driverid=805927") though, but it doesn't mention anything about Core2 support. Also, there is a BIOS update on [_**Acer Support**_]("http://support.acer-euro.com/drivers/downloads_gd.html"), but it doesn't say what it covers.

---

### Post by Rammia on 2009-06-14
:mrgreen: Hi!
I am not running the same OS, in fact, I have just discovered this Ubuntu by a search for information about my motherboard. >.>
Anyhow, I did want to say that I have the same motherboard, or, it would seem I have the same one, since I have the same information in the same fields, ACER ERC410M.
My computer does have dual cpus@ 3.0Ghz ea, so you should be able to upgrade to dual core. Mine is the Aspire E500, so I expect this is the same motherboard. I was trying to find out the motherboard type i.e. ATX, or what, but am glad I ran onto your post, because, hopefully this helps a bit.

---

### Post by directhex on 2009-06-14
Okay, I've done some fishing about, and here's the bad news: Your motherboard is not compatible with "Pentium Dual Core" chips.

Your motherboard chipset is an ATI Radeon XPress 200: [http://ati.amd.com/products/radeonxpress200intel/index.html](http://ati.amd.com/products/radeonxpress200intel/index.html). It's a custom Acer board, which is why you won't find much info about it on the web. Here's the best I found: [www.jhcs.com.au/E500ESS2.pdf](www.jhcs.com.au/E500ESS2.pdf)

It should work with Pentium D chips (which are dual core and based on the P4 design), but not Pentium Dual Core chips (which are based on the Core 2 design).

---

### Post by Rammia on 2009-06-15
I am sorry, I should have been more specific. That is what I have, pentium D dual core 3.0, but under one of the specs programs I have it put pentium 4 class into parentheses, so I didn't realise a difference. I would like to say that, though I am unsure if it was an assembly flaw, or whether it has to do with the board, it runs really quite warm most of the time, so if you upgrade to a pentium D, make sure to use good thermal paste. I am considering taking apart mine and replacing what is there, but am concerned they used the kind that hardens. hope not, though. :mrgreen:

---

### Post by directhex on 2009-06-15
> **Rammia said:**
> I am sorry, I should have been more specific. That is what I have, pentium D dual core 3.0, but under one of the specs programs I have it put pentium 4 class into parentheses, so I didn't realise a difference. I would like to say that, though I am unsure if it was an assembly flaw, or whether it has to do with the board, it runs really quite warm most of the time, so if you upgrade to a pentium D, make sure to use good thermal paste. I am considering taking apart mine and replacing what is there, but am concerned they used the kind that hardens. hope not, though. :mrgreen:

They won't have used thermal epoxy - so worst-case is it's the kind that goes a bit crusty. Just clean it off & re-apply a decent paste.

---

### Post by The Real Dave on 2009-06-15
Ok, thank you so much =] Saved me from wasting &#8364;50. So I should be looking for a Pentium D dual core, as apposed to the Pentium Dual Core. 

Thanks guys =] But one final note, if I was to find a [_**similar Pentium D**_]("http://www.amazon.co.uk/gp/product/B0012IKAZ4/sr=1-12/qid=1245054577/ref=olp_product_details?ie=UTF8&me=&qid=1245054577&sr=1-12&seller="), would my 300Watt PSU be powerfull enough to run everything? I also have 2 SATAII 7K2 Drives, a DVD-/+RW, and a DVD-ROM drive. Will I have enough power? Or will I have to upgrade that too?

---

### Post by directhex on 2009-06-15
> **The Real Dave said:**
> Ok, thank you so much =] Saved me from wasting €50. So I should be looking for a Pentium D dual core, as apposed to the Pentium Dual Core. 

Thanks guys =] But one final note, if I was to find a [_**similar Pentium D**_]("http://www.amazon.co.uk/gp/product/B0012IKAZ4/sr=1-12/qid=1245054577/ref=olp_product_details?ie=UTF8&me=&qid=1245054577&sr=1-12&seller="), would my 300Watt PSU be powerfull enough to run everything? I also have 2 SATAII 7K2 Drives, a DVD-/+RW, and a DVD-ROM drive. Will I have enough power? Or will I have to upgrade that too?

I'll be honest with you - I wouldn't personally. Pentium D is a VERY hungry little chip (about 130W under load, all by itself) - but if you don't have any plug-in graphics card, you're probably okay (i.e. you can get away with it using onboard graphics). If you were using a PCIe graphics card, I'd be very concerned about a 300W supply, especially given the low-efficiency low-quality supplies generally used in OEM computers.

---

### Post by The Real Dave on 2009-06-15
How bout a Celeron Dual Core chip? Are they better? My board should support them ya?

---

### Post by directhex on 2009-06-15
> **The Real Dave said:**
> How bout a Celeron Dual Core chip? Are they better? My board should support them ya?

They are better - but not compatible. Dual-core Celeron chips are all Core 2 based, which you can't use.

---

### Post by The Real Dave on 2009-06-15
Thanks for your advice mate. I think I'm just gonna stay with my PIV. However, if I upgraded the graphics card,(maybe [_**this**_]("http://www.amazon.co.uk/exec/obidos/ASIN/B00172H1UC/ref=ord_cart_shr?_encoding=UTF8&m=A17AS5ETPMZ9A1")?) I reckon it would take some of the strain off my CPU when I'm gaming. 

Also, if I used the HS i mentioned in the first post ([_**this**_]("http://www.amazon.co.uk/exec/obidos/ASIN/B000KB96QS/ref=ord_cart_shr?_encoding=UTF8&m=A17AS5ETPMZ9A1")), would it be complete overkill? My chip is running at around 50C idle and 60-65 under load, which is a bit hot for my liking. But would I be better off with a cheaper model? Is there such a thing as having your CPU too cold?

---

### Post by directhex on 2009-06-15
> **The Real Dave said:**
> Thanks for your advice mate. I think I'm just gonna stay with my PIV. However, if I upgraded the graphics card,(maybe [_**this**_]("http://www.amazon.co.uk/exec/obidos/ASIN/B00172H1UC/ref=ord_cart_shr?_encoding=UTF8&m=A17AS5ETPMZ9A1")?) I reckon it would take some of the strain off my CPU when I'm gaming.

An upgraded graphics card would be a definite improvement for games, even enough to give a real lease of life to your old chip - but a 34xx series is barely an upgrade, and you're starting to enter the danger area for power supplies.

One thing to consider is that your motherboard can take a PCI Express graphics card - as used by all the fastest cards in the world - so if you were to buy a beefy power supply and a beefy graphics card, they could be recycled into your next "new" computer. For graphics cards for gaming, I'd consider anything less than a GeForce 9600GT or a Radeon 3850 to be a waste of money (both weigh in at £60+)

> Also, if I used the HS i mentioned in the first post ([_**this**_]("http://www.amazon.co.uk/exec/obidos/ASIN/B000KB96QS/ref=ord_cart_shr?_encoding=UTF8&m=A17AS5ETPMZ9A1")), would it be complete overkill? My chip is running at around 50C idle and 60-65 under load, which is a bit hot for my liking. But would I be better off with a cheaper model? Is there such a thing as having your CPU too cold?

No, there's no such thing as too cold. I'd definitely look at an upgraded heatsink given the numbers you state.

---

### Post by The Real Dave on 2009-06-15
> No, there's no such thing as too cold. I'd definitely look at an upgraded heatsink given the numbers you state.

Ya, I thought it was too hot alright. I mean like I know the PIV is, was and always will be a hot chip, but 65C under load is a bit much like. Im definately gonna invest in that cooler. 

As for the graphics card, if its not gonna be much of an improvement, again, dont think I'll bother. My current PC is gonna be with me quite a while yet, and at the moment, I cant afford to upgrade both card and PSU :( 

I think for the moment, I'll focus on upgrading my server, as apposed to my main pc, altough, I'm gonna have to improve cooling wise, expecially for my hard drives. 

Thanks a million mate, you've saved me quite a bit of money, which can now be spent on cooling :lolflag: 

I gotta say, its really usefull to have forums like these, expecially in my case, with so little info being available on my PC. 

So once again mate, thank you for your solid advice =]

**Edit:** Speaking of cooling, which would be a better choice between these two coolers

_**[Artic Cooling Freezer 7 Pro]("http://www.amazon.co.uk/exec/obidos/ASIN/B000KB96QS/ref=ord_cart_shr?_encoding=UTF8&m=A17AS5ETPMZ9A1")**_

_**[Thermaltake Silent 775D]("http://www.amazon.co.uk/exec/obidos/ASIN/B000MTET3S/ref=ord_cart_shr?_encoding=UTF8&m=A17AS5ETPMZ9A1")**_

Personally I reckon the Freezer 7 Pro, it says on their site that it can keep an Quad at 52C

[IMG]http://www.arctic-cooling.com/catalog/images/userfiles/image/Charts/Freezer7Pro_chart.gif[/IMG]

---

### Post by directhex on 2009-06-15
I haven't used either cooler, so I'm in no position to judge either way

---

### Post by The Real Dave on 2009-06-15
> **directhex said:**
> I haven't used either cooler, so I'm in no position to judge either way

Alright mate, fair enough. Thanks a million :D

---

