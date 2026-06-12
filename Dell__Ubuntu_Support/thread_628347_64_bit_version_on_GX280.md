---
title: "64 bit version on GX280"
date: 2007-12-01
forum: Dell  Ubuntu Support
---

### Post by hezish on 2007-12-01
hi all,

I have few problem installing 64 bit version on my machine.

after installing it  i get  2.6.22-14-generic intalled.
 
when i check lshw i get:

WARNING: you should run this program as super-user.
hezi-desktop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3326MB
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 3.00GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm syscall nx x86-64 constant_tsc pni monitor ds_cpl est cid cx16 xtpr

someone have an idea? what i did wrong?

Thanks.

---

### Post by hezish on 2007-12-03
help?????

---

### Post by saru411 on 2007-12-04
i dont think your chip is a 64 bit chip......does it say anything about it being 64bit on the info you got from dell? how about the id number for it. that could help me decide if its a 64 bit processor. what errors are you getting. just listing the output of lshw isnt helping me understand what the problem is.

---

