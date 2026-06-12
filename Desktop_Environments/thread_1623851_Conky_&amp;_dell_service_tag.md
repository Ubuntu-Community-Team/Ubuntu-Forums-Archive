---
title: "Conky &amp; dell service tag"
date: 2010-11-17
forum: Desktop Environments
---

### Post by Michael Deats on 2010-11-17
Hi all,

I hope this is the correct forum to post in. I'm looking for some help with Conky. My group is supporting a number of linux machines, all on Dell.. I'd like to display the machines service tag on the desktop using conky, purely to make it easier for the users to give me the tag when logging calls.

Is this possible?

Thanks very much!

---

### Post by Michael Deats on 2010-11-17
No one? I have tried googling and searching this forum, came up empty handed.

---

### Post by a-user on 2010-11-18
if you could tell me how you can retrieve the service tag in general i could tell you how to set up conky for this. i don't a dell pc.

---

### Post by stinkeye on 2010-11-18
Yes, like **a-user** said, you can use grep etc to display the service tag number if it can be found in a file on the computer.
eg if you had a hidden text file in the home directory named **.service_tag**
with only one line in it saying something like **Dell-12345** you could display with conky using...
```
Your Service Number: ${pre_exec cat ~/.service_tag}
```
Really need a bit more info to help.
See pic for result in a simple conky config.

---

### Post by Michael Deats on 2010-11-18
The dell service tag is like a short serial number used to identify the machine when you log a hardware call with dell.

I've managed to pull the service tag from the bios and put it on top of the wallpaper in windows using this method:

[http://forum.sysinternals.com/printer_friendly_posts.asp?TID=4609](http://forum.sysinternals.com/printer_friendly_posts.asp?TID=4609)

I would like to know if the same thing is possible in Ubuntu.

```

The dell service tag is stored in the bios and can be retrived by using a  WMI query
 Create a new WMI custom field
 in the path textbox enter
 SELECT SerialNumber FROM Win32_BIOS
 this is where the DELL service tag is stored (or it is on our DELLS)

```

---

### Post by a-user on 2010-11-18
oh, well the question is not if this can be done with conky. the question is how you read the still unknown poistion in bios to get the service tag.

well, i can't help you here. but you should google for info about retrieving/reading the bios in linux. look for reading at a given address, not for standard entries, then try to discover the tag.

or maybe you find something directly related to dell servcie + bios + linux.

---

### Post by Michael Deats on 2010-11-19
> **a-user said:**
> oh, well the question is not if this can be done with conky. the question is how you read the still unknown poistion in bios to get the service tag.

well, i can't help you here. but you should google for info about retrieving/reading the bios in linux. look for reading at a given address, not for standard entries, then try to discover the tag.

or maybe you find something directly related to dell servcie + bios + linux.

I've tried google, struggling a bit but I'll try some more :)

EDIT:
Hmm
```

http://www.shainmiley.com/wordpress/?p=66

```EDIT 2:

Okay, used the post about to generate this:

```

# dmidecode 2.9
SMBIOS 2.4 present.
62 structures occupying 2879 bytes.
Table at 0x000F68F0.

Handle 0xDA00, DMI type 218, 251 bytes
OEM-specific Type
    Header and Data:
        DA FB 00 DA B2 00 0D 5F 1F 37 40 7D 00 00 00 00
        00 7E 00 02 00 00 00 40 00 04 00 01 00 41 00 04
        00 00 00 90 00 05 00 00 00 91 00 05 00 01 00 92
        00 05 00 02 00 65 00 06 00 00 00 66 00 06 00 01
        00 5E 00 07 00 01 00 5F 00 07 00 00 00 F1 00 08
        00 00 00 F2 00 08 00 01 00 F3 00 08 00 02 00 0F
        00 09 00 00 00 11 00 09 00 01 00 05 00 09 00 02
        00 12 00 09 00 03 00 06 00 09 00 04 00 07 00 0A
        00 00 00 0B 00 0A 00 01 00 0C 00 0A 00 02 00 0D
        00 0A 00 03 00 89 01 0B 00 00 00 8A 01 0B 00 01
        00 42 00 0C 00 01 00 43 00 0C 00 00 00 55 00 0D
        00 00 00 6D 00 0D 00 01 00 16 02 0D 00 02 00 98
        01 0D 00 03 00 0A 01 0E 00 01 00 0B 01 0E 00 00
        00 2D 00 0F 00 02 00 27 01 0F 00 03 00 6E 00 0F
        00 01 00 2E 00 0F 00 00 00 11 01 10 00 00 00 10
        01 10 00 01 00 FF FF 00 00 00 00

Handle 0xDA01, DMI type 218, 251 bytes
OEM-specific Type
    Header and Data:
        DA FB 01 DA B2 00 0D 5F 1F 37 40 F0 00 11 00 01
        00 ED 00 11 00 00 00 41 01 12 00 01 00 40 01 12
        00 00 00 47 01 13 00 01 00 46 01 13 00 00 00 4A
        01 14 00 00 00 4B 01 14 00 01 00 52 01 15 00 01
        00 53 01 15 00 00 00 80 01 16 00 01 00 7F 01 16
        00 00 00 7C 01 17 00 01 00 7B 01 17 00 00 00 7E
        01 18 00 01 00 7D 01 18 00 00 00 92 01 19 00 00
        00 91 01 19 00 01 00 94 01 1A 00 00 00 93 01 1A
        00 01 00 86 01 1B 00 01 00 85 01 1B 00 00 00 82
        01 1C 00 01 00 81 01 1C 00 00 00 84 01 1D 00 01
        00 83 01 1D 00 00 00 9B 01 1E 00 00 00 9C 01 1E
        00 01 00 9D 01 1E 00 02 00 9E 01 1E 00 03 00 8D
        01 1F 00 00 00 8E 01 1F 00 01 00 EA 00 20 00 00
        00 EB 00 20 00 01 00 EC 00 20 00 02 00 28 00 21
        00 00 00 29 00 21 00 01 00 2A 00 21 00 02 00 2B
        00 22 00 00 00 FF FF 00 00 00 00

Handle 0xDA02, DMI type 218, 251 bytes
OEM-specific Type
    Header and Data:
        DA FB 02 DA B2 00 0D 5F 1F 37 40 2C 00 23 00 00
        00 E7 00 24 00 01 00 E6 00 24 00 00 00 0E 01 25
        00 01 00 0F 01 25 00 00 00 9B 00 26 00 01 00 9C
        00 26 00 00 00 87 00 27 00 01 00 88 00 27 00 00
        00 4D 01 28 00 01 00 4C 01 28 00 00 00 51 01 29
        00 00 00 50 01 29 00 01 00 87 01 2A 00 00 00 88
        01 2A 00 01 00 01 01 2B 00 00 00 02 01 2B 00 01
        00 04 01 2B 00 02 00 37 01 2C 00 00 00 38 01 2C
        00 01 00 D9 01 2D 00 01 00 D8 01 2D 00 00 00 C1
        01 2E 00 00 00 C3 01 2E 00 01 00 C2 01 2E 00 02
        00 DF 01 2F 00 01 00 DE 01 2F 00 00 00 EA 01 30
        00 00 00 EB 01 30 00 01 00 EC 01 31 00 00 00 ED
        01 31 00 01 00 00 02 32 00 00 00 01 02 32 00 01
        00 45 01 45 01 01 00 44 01 44 01 00 00 00 80 00
        80 01 00 00 A0 00 A0 01 00 05 80 05 80 01 00 76
        01 76 01 01 00 FF FF 00 00 00 00

Handle 0xDA03, DMI type 218, 65 bytes
OEM-specific Type
    Header and Data:
        DA 41 03 DA B2 00 0D 5F 1F 37 40 75 01 75 01 01
        00 E3 01 E3 01 00 00 E1 01 E1 01 01 00 E2 01 E2
        01 02 00 01 F0 01 F0 00 00 02 F0 02 F0 00 00 03
        F0 03 F0 00 00 04 F0 04 F0 00 00 FF FF 00 00 00
        00

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: Dell Inc.
    Version: A13
    Release Date: 07/28/2008
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 2048 kB
    Characteristics:
        ISA is supported
        PCI is supported
        PC Card (PCMCIA) is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        3.5"/720 KB floppy services are supported (int 13h)
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 1.3
    Firmware Revision: 1.3

Handle 0x0100, DMI type 1, 27 bytes
System Information
    Manufacturer: Dell Inc.
    Product Name: Latitude D630                   
    Version: Not Specified
    Serial Number: 1VP1D3J
    UUID: 44454C4C-5600-1050-8031-B1C04F44334A
    Wake-up Type: Power Switch
    SKU Number: Not Specified
    Family:  

Handle 0x0200, DMI type 2, 9 bytes
Base Board Information
    Manufacturer: Dell Inc.
    Product Name:       
    Version:    
    Serial Number: .1VP1D3J.              .

Handle 0x0300, DMI type 3, 13 bytes
Chassis Information
    Manufacturer: Dell Inc.
    Type: Portable
    Lock: Not Present
    Version: Not Specified
    Serial Number: 1VP1D3J
    Asset Tag: Not Specified
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None

Handle 0x0301, DMI type 126, 13 bytes
Inactive

Handle 0x0400, DMI type 4, 40 bytes
Processor Information
    Socket Designation: Microprocessor
    Type: Central Processor
    Family: <OUT OF SPEC>
    Manufacturer: Intel
    ID: FB 06 00 00 FF FB EB BF
    Version: Not Specified
    Voltage: 3.3 V
    External Clock: 200 MHz
    Max Speed: 2000 MHz
    Current Speed: 2000 MHz
    Status: Populated, Enabled
    Upgrade: None
    L1 Cache Handle: 0x0700
    L2 Cache Handle: 0x0701
    L3 Cache Handle: Not Provided
    Serial Number: Not Specified
    Asset Tag: Not Specified
    Part Number: Not Specified
    Core Count: 2
    Core Enabled: 2
    Thread Count: 2
    Characteristics:
        64-bit capable

Handle 0x0700, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Not Specified
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Back
    Location: Internal
    Installed Size: 32 KB
    Maximum Size: 32 KB
    Supported SRAM Types:
        Unknown
    Installed SRAM Type: Unknown
    Speed: Unknown
    Error Correction Type: None
    System Type: Data
    Associativity: 4-way Set-associative

Handle 0x0701, DMI type 7, 19 bytes
Cache Information
    Socket Designation: Not Specified
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Varies With Memory Address
    Location: Internal
    Installed Size: 4096 KB
    Maximum Size: 4096 KB
    Supported SRAM Types:
        Pipeline Burst
    Installed SRAM Type: Pipeline Burst
    Speed: 15 ns
    Error Correction Type: None
    System Type: Unified
    Associativity: Other

Handle 0x0800, DMI type 126, 9 bytes
Inactive

Handle 0x0801, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: SERIAL1
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: DB-9 male
    Port Type: Serial Port 16550A Compatible

Handle 0x0803, DMI type 126, 9 bytes
Inactive

Handle 0x0804, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: USB
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: Access Bus (USB)
    Port Type: USB

Handle 0x0805, DMI type 126, 9 bytes
Inactive

Handle 0x0806, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: MONITOR
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: DB-15 female
    Port Type: Video Port

Handle 0x0808, DMI type 126, 9 bytes
Inactive

Handle 0x080A, DMI type 126, 9 bytes
Inactive

Handle 0x080B, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: FireWire
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: IEEE 1394
    Port Type: Firewire (IEEE P1394)

Handle 0x080C, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Modem
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: RJ-11
    Port Type: Modem Port

Handle 0x080D, DMI type 8, 9 bytes
Port Connector Information
    Internal Reference Designator: Ethernet
    Internal Connector Type: None
    External Reference Designator: Not Specified
    External Connector Type: RJ-45
    Port Type: Network Port

Handle 0x0900, DMI type 9, 13 bytes
System Slot Information
    Designation: PCMCIA 0
    Type: 32-bit PC Card (PCMCIA)
    Current Usage: Available
    Length: Other
    ID: Adapter 0, Socket 0
    Characteristics:
        5.0 V is provided
        3.3 V is provided
        PC Card-16 is supported
        Cardbus is supported
        Zoom Video is supported
        Modem ring resume is supported

Handle 0x0902, DMI type 126, 13 bytes
Inactive

Handle 0x0A00, DMI type 10, 6 bytes
On Board Device Information
    Type: Video
    Status: Enabled
    Description: Quadro NVS 135M               

Handle 0x0A01, DMI type 10, 6 bytes
On Board Device Information
    Type: Sound
    Status: Enabled
    Description: Sigmatel 9205

Handle 0x0B00, DMI type 11, 5 bytes
OEM Strings
    String 1: Dell System
    String 2: 5[0003]
    String 3: 13[PP18L]

Handle 0x0D00, DMI type 13, 22 bytes
BIOS Language Information
    Installable Languages: 1
        en|US|iso8859-1
    Currently Installed Language: en|US|iso8859-1

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 4 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x1100, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM_A
    Bank Locator: Not Specified
    Type: DDR
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 7F7F7F0B00000000
    Serial Number: ED37232A
    Asset Tag: 000742
    Part Number: NT1GT64U8HB0BN-3C 

Handle 0x1101, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x1000
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 1024 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM_B
    Bank Locator: Not Specified
    Type: DDR
    Type Detail: Synchronous
    Speed: 667 MHz (1.5 ns)
    Manufacturer: 7F7F7F0B00000000
    Serial Number: C6372326
    Asset Tag: 000742
    Part Number: NT1GT64U8HB0BN-3C 

Handle 0x1301, DMI type 19, 15 bytes
Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Array Handle: 0x1000
    Partition Width: 0

Handle 0x1401, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x1100
    Memory Array Mapped Address Handle: 0x1301
    Partition Row Position: 1
    Interleave Position: 1
    Interleaved Data Depth: 8

Handle 0x1411, DMI type 126, 19 bytes
Inactive

Handle 0x1402, DMI type 20, 19 bytes
Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x0007FFFFFFF
    Range Size: 2 GB
    Physical Device Handle: 0x1101
    Memory Array Mapped Address Handle: 0x1301
    Partition Row Position: 1
    Interleave Position: 2
    Interleaved Data Depth: 8

Handle 0x1412, DMI type 126, 19 bytes
Inactive

Handle 0x1500, DMI type 21, 7 bytes
Built-in Pointing Device
    Type: Touch Pad
    Interface: Bus Mouse
    Buttons: 2

Handle 0x1600, DMI type 22, 26 bytes
Portable Battery
    Location: Sys. Battery Bay
    Manufacturer: Sony            
    Name: DELL KP42884    
    Design Capacity: 52000 mWh
    Design Voltage: 11100 mV
    SBDS Version: 1.0
    Maximum Error: 8%
    SBDS Serial Number: 75CE
    SBDS Manufacture Date: 2008-04-06
    SBDS Chemistry: LION            
    OEM-specific Information: 0x00000001

Handle 0x1601, DMI type 126, 26 bytes
Inactive

Handle 0x1602, DMI type 126, 26 bytes
Inactive

Handle 0x1B00, DMI type 27, 12 bytes
Cooling Device
    Type: Fan
    Status: OK
    OEM-specific Information: 0x0000DD00

Handle 0x1C00, DMI type 28, 20 bytes
Temperature Probe
    Description: CPU Internal Temperature
    Location: Processor
    Status: OK
    Maximum Value: 127.0 deg C
    Minimum Value 0.0 deg C
    Resolution: 1.000 deg C
    Tolerance: 0.5 deg C
    Accuracy: Unknown
    OEM-specific Information: 0x0000DC00

Handle 0x2000, DMI type 32, 11 bytes
System Boot Information
    Status: No errors detected

Handle 0xB000, DMI type 176, 5 bytes
OEM-specific Type
    Header and Data:
        B0 05 00 B0 2F

Handle 0xB100, DMI type 177, 12 bytes
OEM-specific Type
    Header and Data:
        B1 0C 00 B1 07 00 00 00 00 00 00 00

Handle 0xB200, DMI type 178, 6 bytes
OEM-specific Type
    Header and Data:
        B2 06 00 B2 99 99

Handle 0xD000, DMI type 208, 10 bytes
OEM-specific Type
    Header and Data:
        D0 0A 00 D0 01 04 FE 00 F9 01

Handle 0xD100, DMI type 126, 12 bytes
Inactive

Handle 0xD200, DMI type 210, 12 bytes
OEM-specific Type
    Header and Data:
        D2 0C 00 D2 F8 03 04 03 06 80 04 05

Handle 0xD800, DMI type 216, 9 bytes
OEM-specific Type
    Header and Data:
        D8 09 00 D8 01 03 01 F0 03
    Strings:
        NVidia Corp.         
         
        060.086.068.000.016.000  

Handle 0xD900, DMI type 217, 8 bytes
OEM-specific Type
    Header and Data:
        D9 08 00 D9 01 02 01 03
    Strings:
        US-101
        Proprietary

Handle 0xDB00, DMI type 219, 9 bytes
OEM-specific Type
    Header and Data:
        DB 09 00 DB 03 01 02 03 FF
    Strings:
        System Device Bay
        Floppy, Battery, CD-ROM, CD-RW, DVD, DVD+RW, DVD+/-RW, Hard Disk, BLU-RAY
        CDRW+DVD  

Handle 0xDB80, DMI type 126, 9 bytes
Inactive

Handle 0xDB81, DMI type 126, 9 bytes
Inactive

Handle 0x8100, DMI type 129, 8 bytes
OEM-specific Type
    Header and Data:
        81 08 00 81 01 01 02 01
    Strings:
        Intel_ASF
        Dell_ASF_001

Handle 0xDC00, DMI type 220, 22 bytes
OEM-specific Type
    Header and Data:
        DC 16 00 DC 01 F0 00 00 02 F0 00 00 00 00 03 F0
        04 F0 00 00 00 00

Handle 0xDD00, DMI type 221, 19 bytes
OEM-specific Type
    Header and Data:
        DD 13 00 DD 00 00 00 00 00 00 00 00 00 00 00 00
        00 00 00

Handle 0xD400, DMI type 212, 47 bytes
OEM-specific Type
    Header and Data:
        D4 2F 00 D4 74 00 75 00 00 10 2D 2E 5C 00 78 BF
        40 5D 00 78 BF 00 2D 01 1D EF 10 2E 01 1D EF 00
        08 00 1D DF 00 03 00 1D DF 00 FF FF 00 00 00

Handle 0xD401, DMI type 212, 17 bytes
OEM-specific Type
    Header and Data:
        D4 11 01 D4 74 00 75 00 03 40 49 4A FF FF 00 00
        00

Handle 0xDE00, DMI type 222, 16 bytes
OEM-specific Type
    Header and Data:
        DE 10 00 DE 01 02 FF FF 00 00 00 00 00 00 00 01

Handle 0x7F00, DMI type 127, 4 bytes
End Of Table

```Now I'm interested in this area:

```
[FONT=monospace]
[/FONT]System Information
    Manufacturer: Dell Inc.
    Product Name: Latitude D630                   
    Version: Not Specified
    Serial Number: 1VP1D3J
    UUID: 44454C4C-5600-1050-8031-B1C04F44334A
    Wake-up Type: Power Switch
    SKU Number: Not Specified
    Family:[FONT=Verdana]
[/FONT]
```Within that section specifically this:
> **Serial Number: 1VP1D3J**Now my issue is that when you run **dmidecode | grep "Serial Number:"** it returns multiple entries of the "Serial Number:" field - how can I grep it so that it only displays that one serial number entry so that I can display it with conky?

---

### Post by stinkeye on 2010-11-19
There's probably a better way of doing it but with my limited knowlegde this works.
```
dmidecode | grep -A 7 "System Information" | grep "Serial Number:" | awk '{print $3}'
```

---

### Post by Michael Deats on 2010-11-19
> **stinkeye said:**
> There's probably a better way of doing it but with my limited knowlegde this works.
```
dmidecode | grep -A 7 "System Information" | grep "Serial Number:" | awk '{print $3}'
```

This works perfectly! How would one go about incorporating this into conky? I'm very limited in my knowledge with conky, and all the guides I find are the "install this then paste this into .conkyrc" - so it does not really explain the structure or syntax of the file.

Thanks so much for the help you guys have given so far!

---

### Post by stinkeye on 2010-11-19
Firstly, after reading the manual page for dmidecode you can use the -s
option with dmidecode to get the info you need with
```
sudo dmidecode -s system-serial-number
```
Hope that's showing the right serial number.


Because you can't run sudo commands from within conky you have to get rid of the need for root access to issue the command.
```
sudo chmod u+s /usr/sbin/dmidecode
```

You should be able to use dmidecode in the terminal now without the need for sudo.

Now to show the output in conky you put this line in your conky config below
the word "TEXT"
```
${pre_exec dmidecode -s system-serial-number}
```
The pre_exec variable executes a shell command one time before conky displays anything and puts output as text.
This is used when the output of the command doesn't change so it doesn't need to run every time conky updates. 
The update interval of conky is determined by **update_interval** in the config.


If you need help in creating a conky config let me know:
* If you want anything else displayed
* Color of the backgound
* Size and color of text
* Position on screen eg top left, bottom right


This config will display as in pic.
```
background yes
update_interval 10.0
total_run_times 0

own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 000000
double_buffer yes
minimum_size 60 5
   
alignment br

gap_x 5 
gap_y 10 

use_xft yes
xftfont Monospace:size=10
xftalpha 0.8
uppercase no
override_utf8_locale yes
use_spacer right
text_buffer_size 256

default_color ffffff
default_shade_color 333333
default_outline_color 00ff00
draw_shades yes
draw_outline no
draw_borders no


# set to yes if you want all text to be in uppercase
uppercase no

# Subtract file system buffers from used memory?
no_buffers yes

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49

TEXT
S/N:${pre_exec dmidecode -s system-serial-number}
```

Save this as **.conkyrc** in the home directory.


**Few notes**
When "conky" is executed it first looks in the home folder for a **.conkyrc** file.
If there is no .conkyrc it will load the default config at **/etc/conky/conky.conf**


You can also name your config file anything you want and start with
```
conky -c /path/to/your/config
```

It is also recommended to delay the start of conky at boot when using gnome
eg```
#!/bin/bash
#start Conky with a 20 second delay
sleep 20
conky
```

---

### Post by Michael Deats on 2010-11-21
> **stinkeye said:**
> Firstly, after reading the manual page for dmidecode you can use the -s
option with dmidecode to get the info you need with
```
sudo dmidecode -s system-serial-number
```Hope that's showing the right serial number.


Because you can't run sudo commands from within conky you have to get rid of the need for root access to issue the command.
```
sudo chmod u+s /usr/sbin/dmidecode
```You should be able to use dmidecode in the terminal now without the need for sudo.

Now to show the output in conky you put this line in your conky config below
the word "TEXT"
```
${pre_exec dmidecode -s system-serial-number}
```If you need help in creating a conky config let me know:
* If you want anything else displayed
* Color of the backgound
* Size and color of text
* Position on screen eg top left, bottom right


This config will display as in pic.
```
background yes
update_interval 10.0
total_run_times 0

own_window yes
own_window_type normal
own_window_transparent no
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour 000000
double_buffer yes
minimum_size 60 5
   
alignment br

gap_x 5 
gap_y 10 

use_xft yes
xftfont Monospace:size=10
xftalpha 0.8
uppercase no
override_utf8_locale yes
use_spacer right
text_buffer_size 256

default_color ffffff
default_shade_color 333333
default_outline_color 00ff00
draw_shades yes
draw_outline no
draw_borders no


# set to yes if you want all text to be in uppercase
uppercase no

# Subtract file system buffers from used memory?
no_buffers yes

# colours
#off white
color1 BDAC88

# cream
color2 D2B16A

# cyan
#color3 08A1A1

# bluemoon
color3 919FAA

# yellow
color4 F1BC49

# Green
color5 00940F

#dark cyan
color6 074C4C


#grey
color7 6b6b6b

#orange
color8 AF560D

#yellow
color9 F1BC49

TEXT
S/N:${pre_exec dmidecode -s system-serial-number}
```Save this as **.conkyrc** in the home directory.


**Few notes**
When "conky" is executed it first looks in the home folder for a **.conkyrc** file.
If there is no .conkyrc it will load the default config at **/etc/conky/conky.conf**


You can also name your config file anything you want and start with
```
conky -c /path/to/your/config
```It is also recommended to delay the start of conky at boot when using gnome
eg```
#!/bin/bash
#start Conky with a 20 second delay
sleep 20
conky
```

Thanks for the help so far! I'm going to have fun with this when I get back to my test machine :P Btw, out of curiosity - why is it recommended to start conky with the 20 sec delay?

---

### Post by stinkeye on 2010-11-21
> **Michael Deats said:**
> Thanks for the help so far! I'm going to have fun with this when I get back to my test machine :P Btw, out of curiosity - why is it recommended to start conky with the 20 sec delay?
When using gnome you need to give time for the desktop to load otherwise Conky sometimes doesn't display properly.

---

### Post by randumnumber on 2010-11-21
Here is a link to the Man page for conky:
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

Here is a link for all of the commands and syntax on how to use them available in a standard conky install:
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Some examples conky scripts:
[http://ubuntuforums.org/showthread.php?t=281865&page=50](http://ubuntuforums.org/showthread.php?t=281865&page=50)

And here is a script to load conky 10 seconds after boot.. to ensure it loads properly
[http://ubuntuforums.org/showthread.php?t=1475063](http://ubuntuforums.org/showthread.php?t=1475063)

Hopefully this plus the info above will help you make a nice looking conky script.

---

### Post by Michael Deats on 2010-11-22
> **randumnumber said:**
> Here is a link to the Man page for conky:
[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

Here is a link for all of the commands and syntax on how to use them available in a standard conky install:
[http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

Some examples conky scripts:
[http://ubuntuforums.org/showthread.php?t=281865&page=50](http://ubuntuforums.org/showthread.php?t=281865&page=50)

And here is a script to load conky 10 seconds after boot.. to ensure it loads properly
[http://ubuntuforums.org/showthread.php?t=1475063](http://ubuntuforums.org/showthread.php?t=1475063)

Hopefully this plus the info above will help you make a nice looking conky script.

Thanks for the info! Loads of fun to be had with this!

---

