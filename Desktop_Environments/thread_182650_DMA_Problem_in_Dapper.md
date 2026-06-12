---
title: "DMA Problem in Dapper"
date: 2006-05-26
forum: Desktop Environments
---

### Post by pacmannia on 2006-05-26
I try to activate the dma mode for my DVD writer,
 
hdparm -d1 /dev/scd0

but it gives an error;

setting using_dma to 1 (on)
HDIO_SET_DMA failed: Inappropriate ioctl for device

How can I manage to activate the dma ??

---

### Post by jvictor on 2006-05-27
1) Are u running it as sudo hdparm ?
2) Are u sure that /dev/scd0 is ur dvd writer ?

I have a DVD +RW and it shows up as /dev/hdc..  

What make is ur DVD writer ? Is it internal / external ? 

Can u plz post the o/p of 

$sudo hdparm -I /dev/hd*

---

### Post by pacmannia on 2006-05-30
1) Yes I'm running it with root.
2) I am sure that my device is /dev/sdc0

I'm using DELL inspiron 6000 and DVD writer is an internal one.

> 
root@pacmania:/home/pacmania# hdparm -I /dev/scd0

/dev/scd0:
 HDIO_DRIVE_CMD(identify) failed: Input/output error


> 
root@pacmania:/home/pacmania# hdparm -I /dev/sda5

/dev/sda5:

ATA device, with non-removable media
        Model Number:       TOSHIBA MK6026GAX
        Serial Number:      X5BS8133T
        Firmware Revision:  PA202D
Standards:
        Supported: 6 5 4 3
        Likely used: 6
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:  117210240
        device size with M = 1024*1024:       57231 MBytes
        device size with M = 1000*1000:       60011 MBytes (60 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 48     Queue depth: 1
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 8
        Advanced power management level: unknown setting (0x0080)
        Recommended acoustic management value: 254, current value: 128
        DMA: sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 udma4 *udma5
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    NOP cmd
           *    READ BUFFER cmd
           *    WRITE BUFFER cmd
           *    Host Protected Area feature set
           *    Look-ahead
           *    Write cache
           *    Power Management feature set
                Security Mode feature set
           *    SMART feature set
           *    Mandatory FLUSH CACHE command
           *    Device Configuration Overlay feature set
           *    Automatic Acoustic Management feature set
                SET MAX security extension
           *    Advanced Power Management feature set
           *    SMART self-test
           *    SMART error logging
Security:
        Master password revision code = 65534
                supported
        not     enabled
        not     locked
                frozen
        not     expired: security count
        not     supported: enhanced erase
        44min for SECURITY ERASE UNIT.
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct


---

### Post by ChrisC on 2006-05-30
"DMA Problem in Dapper"

It might be better to post this in a Dapper forum.

---

