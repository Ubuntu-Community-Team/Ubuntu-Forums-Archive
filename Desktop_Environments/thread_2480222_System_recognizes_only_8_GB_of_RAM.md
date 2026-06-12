---
title: "System recognizes only 8 GB of RAM"
date: 2022-10-23
forum: Desktop Environments
---

### Post by alro7779 on 2022-10-23
Hi, everyone!

Checking System Monitor I realized that my system is recognizing only half of the total amount of memory; I have 16 GB, but Ubuntu is telling me that I have only 8 GB; the BIOS recognizes the total, so the problem is on the system.

```

$ sudo dmidecode -t memory
# dmidecode 3.4
Getting SMBIOS data from sysfs.
SMBIOS 3.2.1 present.

Handle 0x000C, DMI type 16, 23 bytes
Physical Memory Array    
Location: System Board Or Motherboard    
Use: System Memory    
Error Correction Type: None    
Maximum Capacity: 128 GB    
Error Information Handle: 0x000B    
Number Of Devices: 4

Handle 0x0013, DMI type 17, 40 bytes
Memory Device    
Array Handle: 0x000C    
Error Information Handle: 0x0012    
Total Width: Unknown    
Data Width: Unknown    
Size: No Module Installed    
Form Factor: Unknown    
Set: None    
Locator: DIMM 0    
Bank Locator: P0 CHANNEL A    
Type: Unknown    
Type Detail: Unknown

Handle 0x0015, DMI type 17, 40 bytes
Memory Device    
Array Handle: 0x000C    
Error Information Handle: 0x0014    
Total Width: 64 bits    
Data Width: 64 bits    
Size: 8 GB    
Form Factor: DIMM    
Set: None    
Locator: DIMM 1    
Bank Locator: P0 CHANNEL A    
Type: DDR4    
Type Detail: Synchronous Unbuffered (Unregistered)    
Speed: 2667 MT/s    
Manufacturer: A-DATA Technology    
Serial Number: 9EE40100    
Asset Tag: Not Specified    
Part Number: DDR4 2666               
Rank: 1    
Configured Memory Speed: 2667 MT/s    
Minimum Voltage: 1.2 V    
Maximum Voltage: 1.2 V    
Configured Voltage: 1.2 V

Handle 0x0018, DMI type 17, 40 bytes
Memory Device    
Array Handle: 0x000C    
Error Information Handle: 0x0017    
Total Width: Unknown    
Data Width: Unknown    
Size: No Module Installed    
Form Factor: Unknown    
Set: None    
Locator: DIMM 0    
Bank Locator: P0 CHANNEL B    
Type: Unknown    
Type Detail: Unknown

Handle 0x001A, DMI type 17, 40 bytes
Memory Device    
Array Handle: 0x000C    
Error Information Handle: 0x0019    
Total Width: 64 bits    
Data Width: 64 bits    
Size: 8 GB    
Form Factor: DIMM    
Set: None    
Locator: DIMM 1    
Bank Locator: P0 CHANNEL B    
Type: DDR4    
Type Detail: Synchronous Unbuffered (Unregistered)    
Speed: 2667 MT/s    
Manufacturer: A-DATA Technology    
Serial Number: C0E80100    
Asset Tag: Not Specified    
Part Number: DDR4 2666               
Rank: 1    
Configured Memory Speed: 2667 MT/s    
Minimum Voltage: 1.2 V    
Maximum Voltage: 1.2 V    
Configured Voltage: 1.2 V

```

Any ideas on how I can fix this, guys? I've never had this problem before. I'm using Ubuntu 22.10.
Thanks in advance!

EDIT: 
My CPU is a Ryzen 3 1300x and my MOBO is an Asrock B450M Pro4-F.
  Here more commands:
```

$ sudo lshw -C memory
[sudo] password for alejandro: 
  *-firmware                
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: P2.20
       date: 07/27/2020
       size: 64KiB
       capacity: 16MiB
       capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer acpi usb biosbootspecification uefi
  *-memory
       description: System Memory
       physical id: c
       slot: System board or motherboard
       size: 16GiB
     *-bank:0
          description: [empty]
          product: Unknown
          vendor: Unknown
          physical id: 0
          serial: Unknown
          slot: DIMM 0
     *-bank:1
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2667 MHz (0.4 ns)
          product: DDR4 2666
          vendor: A-DATA Technology
          physical id: 1
          serial: 9EE40100
          slot: DIMM 1
          size: 8GiB
          width: 64 bits
          clock: 2667MHz (0.4ns)
     *-bank:2
          description: [empty]
          product: Unknown
          vendor: Unknown
          physical id: 2
          serial: Unknown
          slot: DIMM 0
     *-bank:3
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 2667 MHz (0.4 ns)
          product: DDR4 2666
          vendor: A-DATA Technology
          physical id: 3
          serial: C0E80100
          slot: DIMM 1
          size: 8GiB
          width: 64 bits
          clock: 2667MHz (0.4ns)
  *-cache:0
       description: L1 cache
       physical id: e
       slot: L1 - Cache
       size: 384KiB
       capacity: 384KiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=1
  *-cache:1
       description: L2 cache
       physical id: f
       slot: L2 - Cache
       size: 2MiB
       capacity: 2MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=2
  *-cache:2
       description: L3 cache
       physical id: 10
       slot: L3 - Cache
       size: 8MiB
       capacity: 8MiB
       clock: 1GHz (1.0ns)
       capabilities: pipeline-burst internal write-back unified
       configuration: level=3

```
```

$ free
               total        used        free      shared  buff/cache   available
Mem:         8063632     1953168     4503976       82352     1606488     5775556
Swap:        4194296           0     4194296

```



[IMG]https://ibb.co/wh1mb4P[/IMG]
[IMG]https://ibb.co/wh1mb4P[/IMG]

---

### Post by TheFu on 2022-10-23
Ryzen is picky about RAM.
* is the RAM vendor/model from the approved RAM list?
* Are all 4 sticks "matched" - i.e. from a set purchased in the same package?  Mismatched RAM has issues.
* A bios from 2020 is old for a Ryzen.  New BIOS firmware isn't available?
I have an Asus B450 and the BIOS date on it is 08/17/2021. It comes with American Megatrends Inc.

This speed seems slow for Ryzen.
Speed: 2667 MT/s    

RAM does fail.  Do other kernels see it? Do other OSes see it?  Does memtest run for 2+ days show no issues?

---

### Post by alro7779 on 2022-10-23
It's solved!!! I had to update BIOS to the latest version.

[[IMG]https://i.ibb.co/NZrT3ww/Screenshot-from-2022-10-23-15-41-04.png[/IMG]]("https://ibb.co/NZrT3ww")

```

$ free               
               total        used        free      shared  buff/cache   available
Mem:        16304152     1651400    13016804       76428     1635948    14289568
Swap:        4194296           0     4194296          

```

Thanks for everything!
[IMG]https://ibb.co/HqSXVMn[/IMG]

---

