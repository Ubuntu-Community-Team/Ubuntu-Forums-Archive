---
title: "Understanding sudo lshw -C memory"
date: 2009-05-17
forum: General Help
---

### Post by paul_2978 on 2009-05-17
Hello all,

My first post here so Hi all!!

I like to keep my posts as simple as possible:

UBUNTU 9.04

Running this command in termainal:

**sudo lshw -C memory**

produces this results:

*-firmware              
       description: BIOS
       vendor: American Megatrends Inc.
       physical id: 0
       version: 07.00T (04/02/01)
       size: 64KiB
       capacity: 192KiB
       capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: 5
       slot: Internal Cache
       size: 128KiB
       capacity: 1MiB
       capabilities: synchronous internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: Internal Cache
       size: 256KiB
       capacity: 1MiB
       capabilities: synchronous internal write-back unified
  *-memory
       description: System memory
       physical id: 1
       size: 1508MiB

Which is great............but can someone guide me to what these actual mean - 


*-cache:0 - IS THIS THE MEMORY ALOCATION I HAVE 3 SLOTS OF RAM????
       description: L1 cache   - MEMORY ALOCATION THIS IS FINE
       physical id: 5 - NOT A CLUE ON THIS ONE
       slot: Internal Cache
       size: 128KiB
       capacity: 1MiB
       capabilities: synchronous internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: 6
       slot: Internal Cache
       size: 256KiB
       capacity: 1MiB
       capabilities: synchronous internal write-back unified
  *-memory
       description: System memory
       physical id: 1
       size: 1508MiB - THIS IS MY TOTAL RAM.

MY RAM IS 400MHZ is there a command that can show me what ram spec im running? any help is greatly appreciated in advance even a url to a good area for "lshw"

Thanks 

Paul

---

### Post by logos34 on 2009-05-17
no, your L1 and L2 cache are on the cpu

> *-memory
description: System memory
physical id: 1
size: 1508MiB 

that's all it outputs?  Normally it lists each bank and dimm slot (occupied or not), i.e.:

 > *-memory:0
       description: System Memory
       physical id: 16
       slot: System board or motherboard
       size: 512MiB
     *-bank:0
          [COLOR="Red"]description: DIMM [empty][/COLOR]
          physical id: 0
          slot: A0
          width: 64 bits
     *-bank:1
          description: DIMM
          physical id: 1
          slot: A1
        [COLOR="Blue"]  size: 512MiB[/COLOR]
          width: 64 bits

there's also 

> cat /proc/meminfo

---

