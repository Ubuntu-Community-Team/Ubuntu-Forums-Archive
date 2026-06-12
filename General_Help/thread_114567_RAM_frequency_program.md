---
title: "RAM frequency program?"
date: 2006-01-08
forum: General Help
---

### Post by Scrufdog on 2006-01-08
I cant seem to find anything to tell me what frequency my RAM is running at. 

in Windows, programs such as CPU-Z, ClockGen, SiSoft Sandra, etc... tell you what frequency the RAM itself is running at. I know memtest86+ does it, but I"m looking for something that works in Linux without boot disks and such.

Any ideas?

---

### Post by Scrufdog on 2006-01-10
anybody?

---

### Post by moffa on 2006-01-10
That information should be in your BIOS when you turn on the computer.  Memtest automatically lists itself in the grub menu - so you shouldn't need boot disks.

Sorry, but I'm a newb too and do not know of any Sisoft Sandra type programs yet.

---

### Post by jasay on 2006-01-10
Are you looking for something like this:```
 *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns) [empty]
             physical id: 2
             slot: CHANNEL A DIMM 1
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns) [empty]
             physical id: 3
             slot: CHANNEL B DIMM 1
             width: 64 bits
             clock: 400MHz (2.5ns)

```

If so try a ```
sudo lshw
``` as in "list hardware."  That should tell you just about anything you want to know about your hardware.

---

### Post by rfruth on 2006-01-10
lshw works great 4 me thanks ! [http://www.rfruth.net/resume/computers/breezy/breezylshw.txt]("http://www.rfruth.net/resume/computers/breezy/breezylshw.txt")

---

### Post by Scrufdog on 2006-01-11
[QUOTE=jasay]Are you looking for something like this:```
 *-memory
          description: System Memory
          physical id: 1000
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 0
             slot: CHANNEL A DIMM 0
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns)
             physical id: 1
             slot: CHANNEL B DIMM 0
             size: 512MB
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:2
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns) [empty]
             physical id: 2
             slot: CHANNEL A DIMM 1
             width: 64 bits
             clock: 400MHz (2.5ns)
        *-bank:3
             description: DIMM SDRAM Synchronous 400 MHz (2.5 ns) [empty]
             physical id: 3
             slot: CHANNEL B DIMM 1
             width: 64 bits
             clock: 400MHz (2.5ns)

```

If so try a ```
sudo lshw
``` as in "list hardware."  That should tell you just about anything you want to know about your hardware.[/QUOTE]

is this Ubuntu specific or will it will in most distributions of Linux?

...and thx, thats what I'm looking for..

---

### Post by Scrufdog on 2006-01-11
nevermind, seems to be a standard package.

Ive been trying to find the RAM speed of my xbox hardware. lshw shows literally everything but that. damnit... heh heh

guess I'll keep searching

---

### Post by Samhain13 on 2007-11-15
Hi, this may have come very, very late but I ran into this thread as it appeared while searching Google for the same thing. Anyway, other than lshw, I also found the **sudo dmidecode** command which give me this, among other things:

```

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A0
        Bank Connections: 0
        Current Speed: 60 ns
        Type: Other SDRAM
        Installed Size: 256 MB (Single-bank Connection)
        Enabled Size: 256 MB (Single-bank Connection)
        Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
        Socket Designation: A1
        Bank Connections: 2
        Current Speed: 60 ns
        Type: Other SDRAM
        Installed Size: 256 MB (Single-bank Connection)
        Enabled Size: 256 MB (Single-bank Connection)
        Error Status: OK

```

I hope you find the info you're looking for from that. :D

---

