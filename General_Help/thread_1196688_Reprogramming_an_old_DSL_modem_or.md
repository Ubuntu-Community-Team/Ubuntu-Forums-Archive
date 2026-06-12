---
title: "Reprogramming an old DSL modem or ???"
date: 2009-06-25
forum: General Help
---

### Post by Divider on 2009-06-25
[B]So i've got a graveyard of towers, laptop, servers and more. But I have recycling bin full of DSL modems. Mostly Netopias and 2wires. 

Anyone know how I could repogram one of these lil babies just for fun? I'd love to see it running a lite distro off of a thumb drive.

I guess where would i start buildin the Firmware?


Is there a TFTP list command or a dumping tool anyone knows about?

I really would like to see one as a linux box. :)

any help is much appreciated. 

-Divider[/B]

---

### Post by Divider on 2009-06-26
24 Hour no reply bump.

---

### Post by t4thfavor on 2009-06-26
You would start by finding out if the hardware supports another firmware, or if the manufacturer has open sourced their current firmware such as the case with the WRT54G. 

You will most likely find that they have a propriatery CPU, and not enough RAM to do anything useful. So try a WRT54G.

---

### Post by Divider on 2009-06-26
Well any Device can be made to support another firmware, take the sony psp for example, the trick is the bootloader for the individual  unit.

More or less what I am asking is there a way to dump the current firmware of a unit, similar to FWCutter for Broadcom B43 Wireless chipsets.

---

### Post by HavocXphere on 2009-06-26
A lot of dsl modems already run linux.

Use nmap's OS detection to check.

e.g. My router says:
> Running: Linux 2.6.X
OS details: Linux 2.6.13 - 2.6.24


Also, try logging into the router with telnet. Usually one can check out hardware specs etc using the cat command & the associated file.
> > cat /proc/cpuinfo
system type             : D-4P-W
processor               : 0
cpu model               : BCM6348 V0.7
BogoMIPS                : 255.59
wait instruction        : no
microsecond timers      : yes
tlb_entries             : 32
extra interrupt vector  : yes
hardware watchpoint     : no
VCED exceptions         : not available
VCEI exceptions         : not available
> 
> >  cat /proc/meminfo
MemTotal:        14040 kB
MemFree:           448 kB
Buffers:          1116 kB
Cached:           6156 kB
SwapCached:          0 kB
Active:           4528 kB
Inactive:         4484 kB
HighTotal:           0 kB
HighFree:            0 kB
LowTotal:        14040 kB
LowFree:           448 kB
SwapTotal:           0 kB
SwapFree:            0 kB
Dirty:               0 kB
Writeback:           0 kB
Mapped:           4124 kB
Slab:             2504 kB
Committed_AS:     6160 kB
PageTables:        396 kB
VmallocTotal:  1048560 kB
VmallocUsed:      1236 kB
VmallocChunk:  1046840 kB
> 


Edit: Also have a look at the tomatoe router firmware.

---

### Post by t4thfavor on 2009-06-26
> **Divider said:**
> Well any Device can be made to support another firmware, take the sony psp for example, the trick is the bootloader for the individual  unit.

More or less what I am asking is there a way to dump the current firmware of a unit, similar to FWCutter for Broadcom B43 Wireless chipsets.

Tell that to my SonicWall It has to have a standard proc, or your just spinning your wheels. With the PSP it used a powerPC chip from IBM if im remrmbering correctly, but if its a like a SonicWall it uses some special purpose CPU with no open spec. I have been around the custom firmware sites since '04, and I assure you every device does not support alt firmware.

---

### Post by Divider on 2009-06-29
> **t4thfavor said:**
> Tell that to my SonicWall It has to have a standard proc, or your just spinning your wheels. With the PSP it used a powerPC chip from IBM if im remrmbering correctly, but if its a like a SonicWall it uses some special purpose CPU with no open spec. I have been around the custom firmware sites since '04, and I assure you every device does not support alt firmware.

and I assure you, if someone programmed for the original device, then custom firmware CAN be made. Well it's good to know you've never actually programmed or even helped develop custom firmware as you stated clearly, "i've been around the sites since '04" clearly stating you've actually never contributed anything.

As for the PSP, it is an ARM architecture, I think you are referring to the recently released PS3.

Your sonicwall uses an NSA-E Multicore Processor if it is a recent one. Why don't you try taking it apart and getting a serial off the chip and punching up your results into google.

---

### Post by t4thfavor on 2009-06-29
heh, good luck then...

---

### Post by Buzzez on 2009-06-29
Yes, you can. But why dont you choose an easier solution ?

---

