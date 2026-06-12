---
title: "Dell PowerEdge 2950 Only Sees"
date: 2011-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kristenannie on 2011-08-31
We have a Dell PowerEdge 2950 running Ubuntu 7.10, 64 bit version.  It has 32 GB RAM installed, but is only seeing approx. 3.75 GB.

I researched this a little and ran the various commands to make sure we are running a 64 bit kernel, etc.  Here are the results of those commands:

db:~$uname -mrs
Linux 2.6.22-14-server x86_64


db:~$ uname -a
Linux moodledb 2.6.22-14-server #1 SMP Sun Oct 14 22:09:15 GMT 2007 x86_64 GNU/Linux


db:~$ free -m
total       used       free     shared    buffers     cached
Mem:         32217      27838       4379          0        505      25474
-/+ buffers/cache:       1858      30359
Swap:         2870          0       2870


When I do a command to see physical memory, I get this:

db:~$ sudo dmidecode --type memory
# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: Multi-bit ECC
    Maximum Capacity: 65280 MB
    Error Information Handle: Not Provided
    Number Of Devices: 8

Handle 0x1100, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: FB-DIMM
    Set: 1
    Locator: DIMM1 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 830B8089830B
    Serial Number: CC9A2044
    Asset Tag: 110746
    Part Number: NT2GT72U4NB1BN-3C 

Handle 0x1101, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: FB-DIMM
    Set: 1
    Locator: DIMM2 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 830B8089830B
    Serial Number: 40A12043
    Asset Tag: 110746
    Part Number: NT2GT72U4NB1BN-3C 

Handle 0x1102, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: FB-DIMM
    Set: 2
    Locator: DIMM3 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 830B8089830B
    Serial Number: C99B2041
    Asset Tag: 110746
    Part Number: NT2GT72U4NB1BN-3C 

Handle 0x1103, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: FB-DIMM
    Set: 2
    Locator: DIMM4 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 830B8089830B
    Serial Number: FA9A2041
    Asset Tag: 110746
    Part Number: NT2GT72U4NB1BN-3C 

Handle 0x1104, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: FB-DIMM
    Set: 3
    Locator: DIMM5 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 802C7FB3802C
    Serial Number: DF7416DC
    Asset Tag: 081109
    Part Number: 36HF51272FZ667H1D6

Handle 0x1105, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: FB-DIMM
    Set: 3
    Locator: DIMM6 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 802C7FB3802C
    Serial Number: DF7416DD
    Asset Tag: 081109
    Part Number: 36HF51272FZ667H1D6

Handle 0x1106, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: FB-DIMM
    Set: 4
    Locator: DIMM7 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 802C7FB3802C
    Serial Number: DD859A20
    Asset Tag: 081108
    Part Number: 72HTS1G72FZ667H1D6

Handle 0x1107, DMI type 17, 28 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 72 bits
    Data Width: 64 bits
    Size: 8192 MB
    Form Factor: FB-DIMM
    Set: 4
    Locator: DIMM8 
    Bank Locator: Not Specified
    Type: DDR2 FB-DIMM
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 802C7FB3802C
    Serial Number: DD859A1F
    Asset Tag: 081108
    Part Number: 72HTS1G72FZ667H1D6


Any ideas?  We are running 64 bit Ubuntu on a 64 bit machine with 32 GB of RAM, but can only see 3.75 GB.

Just in case anyone is curious, we are preparing to install Hyper-V on this box, which is why we have upped the RAM.  We aren't ready to move over though, and I really need to have access to more than 3.75 GB of RAM.  32GB at this point is overkill, but I do need more than 3.75 GB for the services this box is running to perform well.

Thanks,
Kristen

---

