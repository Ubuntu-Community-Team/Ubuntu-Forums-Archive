---
title: "Not sure if this is a problem or not??"
date: 2010-12-26
forum: Desktop Environments
---

### Post by mkmagu on 2010-12-26
I've installed Ubuntu 10.10 as a dual boot with Windows 7 on my desktop I'm able to log into both OS and both work appear to work fine except for 1 thing. When I log into Ubuntu I see this string after my login 
mary-N68SA-M2S-Invalid-entry-length-1-DMI-table-is-broken-Stop:~$ 

I don't think this is correct and wanted to know if there is a way to fix it with out reloading.  I can add applications via the software center but when trying to add Xampp I get the following error

tar (child): xampp-linux-1.7.3a.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now

I don't know if this is related to the above string or that I'm doing something else wrong. 
Thanks in advance!

---

### Post by dabl on 2010-12-26
In a terminal, enter this:

```
sudo dmidecode --type memory
```

What is the output?

---

### Post by mkmagu on 2010-12-26
This is what came back, 

# dmidecode 2.9
SMBIOS 2.5 present.

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
    Error Detecting Method: 64-bit ECC
    Error Correcting Capabilities:
        None
    Supported Interleave: One-way Interleave
    Current Interleave: One-way Interleave
    Maximum Memory Module Size: 4096 MB
    Maximum Total Memory Size: 16384 MB
    Supported Speeds:
        70 ns
        60 ns
        50 ns
    Supported Memory Types:
        Standard
        DIMM
    Memory Module Voltage: 2.9 V
    Associated Memory Slots: 4
        0x0006
        0x0007
        0x0008
        0x0009
    Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A0
    Bank Connections: 0 1
    Current Speed: Unknown
    Type: Other Unknown EDO
    Installed Size: 2048 MB (Double-bank Connection)
    Enabled Size: 2048 MB (Double-bank Connection)
    Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A1
    Bank Connections: None
    Current Speed: Unknown
    Type: Other Unknown EDO
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A2
    Bank Connections: None
    Current Speed: Unknown
    Type: Other Unknown EDO
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
    Socket Designation: A3
    Bank Connections: None
    Current Speed: Unknown
    Type: Other Unknown EDO
    Installed Size: Not Installed
    Enabled Size: Not Installed
    Error Status: OK

Handle 0x001D, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Error Information Handle: Not Provided
    Number Of Devices: 4

Handle 0x001E, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x001D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: A0
    Bank Locator: Bank0/1
    Type: DDR2
    Type Detail: None
    Speed: 800 MHz (1.2 ns)
    Manufacturer: 7F7FB5FFFFFFFFFF
    Serial Number: 30601815
    Asset Tag: None
    Part Number: <BAD INDEX>

Invalid entry length (1). DMI table is broken! Stop.


My system is a barebones from Tigerdirect 
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=7039527&CatId=332](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=7039527&CatId=332)


[LIST]
[*]Biostar N68S+ Motherboard - GeForce 7025, Socket AM2+, USB, LAN, PCIe, MicroATX
[*]AMD Phenom X3 8250e Triple Core Processor HD8250ODJ3BGH - 1.9GHz, Socket AM2+, 1.5MB L2, 2MB L3 Cache, OEM
[*]Centon 2048MB PC6400 DDR2 800MHz Memory
[*]Seagate ST31000520AS Barracuda LP Hard Drive - 1TB, 5900rpm, 32MB, SATA-3G
[*]Raygo R12-40835 ATX Mid-Tower Case - ATX/Micro-ATX 1x External 3.5"  Bays, 4x External 5.25" Bays, 6x Internal 3.5" Bays, 2x Fron USB Ports,  450W PSU Included, Black
[/LIST]

Thanks for the help!

---

### Post by dabl on 2010-12-26
The only other case I can turn up with my google-foo indicates it is not a serious error.  Apparently your BIOS is not reporting the installed memory to the satisfaction of the kernel.  But, unless you have any other indications that there's a memory problem, I'd ignore it.  If there's any doubt, from a booted Live CD you can run the "Memory Test" routine, and just let it run overnight so it gets multiple passes through the memory.

This issue is unrelated to whatever happened with your attempt to install xammp -- that's something else, probably not about your computer system at all.

---

