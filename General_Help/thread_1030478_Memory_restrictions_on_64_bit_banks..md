---
title: "Memory restrictions on 64 bit banks."
date: 2009-01-04
forum: General Help
---

### Post by qazokm on 2009-01-04
I was just curious about the amount of memory I could theoretically install on my system.

Everything I've found leads me to believe that I can install up to 64GiB, but the line from "lshw -c memory" stating that memory capacity is only 3Gib seems to disagree with that finding.

Does my BIOS limit my memory or am I just misinterpreting something?

  > jfrey@Tablet:~$ sudo lshw -c memory
[sudo] password for jfrey: 
  *-firmware              
       description: BIOS
       vendor: Hewlett-Packard
       physical id: 0
       version: F.09 (10/23/2008)
       size: 1MiB
       capabilities: isa pci pnp upgrade shadowing escd cdboot bootselect int5printscreen int9keyboard int14serial int17printer acpi usb agp smartbattery biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: b
       slot: L1 Cache
       size: 256KiB
       capacity: 256KiB
       capabilities: synchronous internal write-back unified
  *-cache:1
       description: L2 cache
       physical id: c
       slot: L2 Cache
       size: 1MiB
       capacity: 1MiB
       capabilities: synchronous internal write-back unified
  *-memory
       description: System Memory
       physical id: d
       slot: System board or motherboard
       size: 3GiB
       capacity: 3GiB
     *-bank:0
          description: SODIMM Synchronous 800 MHz (1.2 ns)
          product: 64T256020EDL2.5C2
          vendor: 0000517F7F7F7F7F
          physical id: 0
          serial: 7F7F7F7F7F510000440843030F0919
          slot: SODIMM 0
          size: 2GiB
          width: 64 bits
          clock: 800MHz (1.2ns)
     *-bank:1
          description: SODIMM Synchronous 800 MHz (1.2 ns)
          product: M4 70T2864QZ3-CF7
          vendor: 00000000000000CE
          physical id: 1
          serial: CE0000000000000002084795582E21
          slot: SODIMM 1
          size: 1GiB
          width: 64 bits
          clock: 800MHz (1.2ns)


---

### Post by ajgreeny on 2009-01-04
In theory, with a 64 bit OS you can use more memory than you're ever likely to be able to install in a computer.  It does depend on the computer hardware and software, however, and what the limit is for the motherboard in the machine.  As I understand it, a 64 bit computer running a 32 bit OS will not show or be able to use more than the approximate 3GB limit of that OS, no matter how much is actually installed on the MB.  It is not totally clear from your post if you have a 64 bit OS.

---

### Post by bodhi.zazen on 2009-01-04
> **ajgreeny said:**
> In theory, with a 64 bit OS you can use more memory than you're ever likely to be able to install in a computer.  It does depend on the computer hardware and software, however, and what the limit is for the motherboard in the machine.  As I understand it, a 64 bit computer running a 32 bit OS will not show or be able to use more than the approximate 3GB limit of that OS, no matter how much is actually installed on the MB.  It is not totally clear from your post if you have a 64 bit OS.

No that is wrong. If you install a 32 bit OS and use a PAE enabled kernel you will be able to see up to 64 Gb of RAM

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

Every 64 bit CPU I have seen is pae enabled, you can check with

```
grep --color=always pae /proc/cpuinfo
```

Otherwise, yes the RAM you can install will most likely be limited by your motherboard.

---

### Post by ajgreeny on 2009-01-04
Thanks, I didn't know that.

---

### Post by bodhi.zazen on 2009-01-04
> **ajgreeny said:**
> Thanks, I didn't know that.

No problem, most people do not ;)

---

