---
title: "Ubuntu 9.10 server don't find all CPU"
date: 2010-01-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lexo on 2010-01-15
Hello,

i'm just installed  ubuntu 9.10 server 64 bits on PowerEdge R410 8Gb RAM with 2 CPU Intel Xeon E5506 Processor (2.13GHz, 4M Cache, 4.86 GT/s QPI), 800MH

"top" command only view 4 CPU instead of 8 :(

I'm testing whis 10.04 alpha 2 and result is the same

Wha'ts the solution please ? Perhaps is it normal ?

```
top - 10:41:29 up 25 min,  1 user,  load average: 0.00, 0.00, 0.00
Tasks: 105 total,   1 running, 104 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.3%sy,  0.0%ni, 99.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   8182048k total,   383928k used,  7798120k free,    70060k buffers
Swap:  1951888k total,        0k used,  1951888k free,   113604k cached
``````
#uname -a
Linux qlhttp1 2.6.31-17-server #54-Ubuntu SMP Thu Dec 10 18:06:56 UTC 2009 x86_64 GNU/Linux
``````
# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 26
model name      : Intel(R) Xeon(R) CPU           E5506  @ 2.13GHz
stepping        : 5
cpu MHz         : 2127.943
cache size      : 4096 KB
physical id     : 1
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 16
initial apicid  : 16
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe sy
bogomips        : 4255.88
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 26
model name      : Intel(R) Xeon(R) CPU           E5506  @ 2.13GHz
stepping        : 5
cpu MHz         : 2127.943
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe sy
bogomips        : 4256.01
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 26
model name      : Intel(R) Xeon(R) CPU           E5506  @ 2.13GHz
stepping        : 5
cpu MHz         : 2127.943
cache size      : 4096 KB
physical id     : 1
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 18
initial apicid  : 18
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe sy
bogomips        : 4255.96
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 26
model name      : Intel(R) Xeon(R) CPU           E5506  @ 2.13GHz
stepping        : 5
cpu MHz         : 2127.943
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 11
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe sy
bogomips        : 4256.01
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management:
``````
# dmidecode 2.9
SMBIOS 2.6 present.
77 structures occupying 4238 bytes.
Table at 0xCF79C000.

Handle 0xDA00, DMI type 218, 11 bytes
OEM-specific Type
        Header and Data:
                DA 0B 00 DA B2 00 17 00 0E 20 00

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
        Vendor: Dell Inc.
        Version: 1.2.4
        Release Date: 11/02/2009
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 4096 kB
        Characteristics:
                ISA is supported
                PCI is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
                5.25"/360 KB floppy services are supported (int 13h)
                5.25"/1.2 MB floppy services are supported (int 13h)
                3.5"/720 KB floppy services are supported (int 13h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
        BIOS Revision: 1.2

Handle 0x0100, DMI type 1, 27 bytes
System Information
        Manufacturer: Dell Inc.
        Product Name: PowerEdge R410
        Version: Not Specified
        Serial Number: 
        UUID: 44454C4C-4A00-1054-8052-C4C04F4C344A
        Wake-up Type: Power Switch
        SKU Number: Not Specified
        Family: Not Specified

Handle 0x0200, DMI type 2, 9 bytes
Base Board Information
        Manufacturer: Dell Inc.
        Product Name: 0N051F
        Version: A04
        Serial Number: ..CN137409BN021F.

Handle 0x0300, DMI type 3, 21 bytes
Chassis Information
        Manufacturer: Dell Inc.
        Type: Rack Mount Chassis
        Lock: Present
        Version: Not Specified
        Serial Number: 
        Asset Tag: Not Specified
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Safe
        Security Status: Unknown
        OEM Information: 0x00000000
        Height: 1 U
        Number Of Power Cords: Unspecified
        Contained Elements: 0

Handle 0x0400, DMI type 4, 40 bytes
Processor Information
        Socket Designation: CPU1
        Type: Central Processor
        Family: Xeon
        Manufacturer: Intel
        ID: A5 06 01 00 FF FB EB BF
        Signature: Type 0, Family 6, Model 26, Stepping 5
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
        Version: Intel(R) Xeon(R) CPU           E5506  @ 2.13GHz
        Voltage: 1.2 V
        External Clock: 4800 MHz
        Max Speed: 3600 MHz
        Current Speed: 2133 MHz
        Status: Populated, Enabled
        Upgrade: <OUT OF SPEC>
        L1 Cache Handle: 0x0700
        L2 Cache Handle: 0x0701
        L3 Cache Handle: 0x0702
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 2
        Thread Count: 4
        Characteristics:
                64-bit capable

Handle 0x0401, DMI type 4, 40 bytes
Processor Information
        Socket Designation: CPU2
        Type: Central Processor
        Family: Xeon
        Manufacturer: Intel
        ID: A5 06 01 00 FF FB EB BF
        Signature: Type 0, Family 6, Model 26, Stepping 5
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
        Version: Intel(R) Xeon(R) CPU           E5506  @ 2.13GHz
        Voltage: 1.2 V
        External Clock: 4800 MHz
        Max Speed: 3600 MHz
        Current Speed: 2133 MHz
        Status: Populated, Idle
        Upgrade: <OUT OF SPEC>
        L1 Cache Handle: 0x0703
        L2 Cache Handle: 0x0704
        L3 Cache Handle: 0x0705
        Serial Number: Not Specified
        Asset Tag: Not Specified
        Part Number: Not Specified
        Core Count: 4
        Core Enabled: 2
        Thread Count: 4
        Characteristics:
                64-bit capable
```

---

### Post by wojox on 2010-01-15
Looks like their dual-core hyperthreaded. Look at the physical id's.

[http://blog.incase.de/index.php/2007/10/17/cpu-feature-flags-and-their-meanings/#comment-1941](http://blog.incase.de/index.php/2007/10/17/cpu-feature-flags-and-their-meanings/#comment-1941)

---

### Post by Rastambul on 2010-01-15
> **wojox said:**
> Looks like their dual-core hyperthreaded. Look at the physical id's.

[http://blog.incase.de/index.php/2007/10/17/cpu-feature-flags-and-their-meanings/#comment-1941](http://blog.incase.de/index.php/2007/10/17/cpu-feature-flags-and-their-meanings/#comment-1941)

  Hi, same problem. I have the same hardware with Ubuntu 9.10. The XEON E5506 is a quadcore CPU, here are the specs:

[http://ark.intel.com/Product.aspx?id=37096](http://ark.intel.com/Product.aspx?id=37096)

---

### Post by Rastambul on 2010-01-15
> **Rastambul said:**
> Hi, same problem. I have the same hardware with Ubuntu 9.10. The XEON E5506 is a quadcore CPU, here are the specs:

[http://ark.intel.com/Product.aspx?id=37096](http://ark.intel.com/Product.aspx?id=37096)

Solved! There's an option in the system BIOS to enable all the cores. Default is dual :confused:

---

### Post by lexo on 2010-01-16
> **Rastambul said:**
> Solved! There's an option in the system BIOS to enable all the cores. Default is dual :confused:
Yes, that's right :)

very thanks

---

