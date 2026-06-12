---
title: "32 bit/ 64 bit installation problem"
date: 2011-02-18
forum: Desktop Environments
---

### Post by CJ_Hudson on 2011-02-18
Hi, I have just installed Ubuntu 64 bit version from 2 CDs successively (one a download from the Ubuntu official source (Karmic Koala 9.10)) and one free with Ubuntu User magazine (10.10) (claiming to be 64 bit) but neither shows up all 4 Gb  of my RAM, they both still only showed 3.1 Gb.
Please, does anyone know why this didn't work? I have an Asus motherboard (P5L-VM1394)and dual-core Intel E2200 processor.

Now I just have to get my netgear wireless card installed and working again!

---

### Post by Grenage on 2011-02-18
The 4GB should be available in the x64 release.  From the terminal:

```
uname -a
```

What does it say?

---

### Post by sikander3786 on 2011-02-18
Check under your Bios and make sure all of your 4 GB RAM is being detected properly there. Might be one of the modules ran bad? Or it is not seated properly into the memory bank?

Aside from that, even if you install 32-bit Ubuntu and it detects RAM > 3 GB, it would automatically install the PAE Kernel for supporting all of your RAM. So thats not the issue I think.

Outputs of these command might also help us.

```
sudo lshw
free -m
```

---

### Post by 3Miro on 2011-02-18
This is an older motherboard, probably doesn't have memory remapping enabled by default. Look into your BIOS setup for the proper settings.

---

### Post by CJ_Hudson on 2011-02-18
Thankyou that is very helpful, I will post the information shortly.
However might I mention I cannot and never have been able to unlock the bios? None of the normal key combinations work!

(Apologies for multiple post below!)

---

### Post by CJ_Hudson on 2011-02-18
> **Grenage said:**
> The 4GB should be available in the x64 release.  From the terminal:

```
uname -a
```

What does it say?

Linux chris-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

..and the further question:


Re: 32 bit/ 64 bit installation problem
Check under your Bios and make sure all of your 4 GB RAM is being detected properly there. Might be one of the modules ran bad? Or it is not seated properly into the memory bank?

Aside from that, even if you install 32-bit Ubuntu and it detects RAM > 3 GB, it would automatically install the PAE Kernel for supporting all of your RAM. So thats not the issue I think.

Outputs of these command might also help us.

Code:

sudo lshw
free -m

Result is (and I assume you only require the first part of this as it looks awefully long,):-

 description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=409D11B0-3C83-DB11-96E5-0018F3213FFD
  *-core
       description: Motherboard
       product: P5L-VM 1394
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: MB-1234567890
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0201 (09/05/2006)
          size: 64KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Pentium(R) Dual CPU E2200 @ 2.20GHz
          serial: To Be Filled By O.E.M.
          slot: LGA 775
          size: 1200MHz
          capacity: 3800MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall x86-64 constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies instruction
     *-memory
          description: System Memory
          physical id: 35
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 1GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 1GiB
             width: 64 bits
        *-bank:2
             description: DIMM SDRAM Synchronous
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
             size: 1GiB
             width: 64 bits
        *-bank:3
             description: DIMM SDRAM Synchronous
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
             size: 1GiB
             width: 64 bits

?
Thanks.

---

### Post by PRC09 on 2011-02-18
From the spec sheet of your motherboard.....



> * Due to general PC architecture, a small amount of memory is reserved for system usage and thus the actual memory size is less than the stated amount. 

---

### Post by sikander3786 on 2011-02-18
You are running 64bit Kernel and whole of your memory is detected here.

> *-memory
description: System Memory
physical id: 35
slot: System board or motherboard
size: 4GiB

And system reserves some memory, some but not 900 MB of it. I couldn't find the output of this one in your above post.

```
free -m
```

---

### Post by CJ_Hudson on 2011-02-18
Here it is:

   total       used       free     shared    buffers     cached
Mem:          3145        873       2271          0         79        202
-/+ buffers/cache:        590       2554
Swap:         3906          0       3906

---

### Post by sikander3786 on 2011-02-18
Ok I can see the output now.

Which graphics card is there? Motherboard integrated one? Are you sharing your memory with your graphics card?

---

### Post by CJ_Hudson on 2011-02-18
I've got an nVidia 8400 GS 256 Mb graphics card but, by the way, the hardware updater doesn't seem to recognise it. (unless in Ubuntu 64 bit it runs as native, which I doubt!)

---

### Post by PRC09 on 2011-02-18
In regards to the memory from the Asus manual........I personally have seen the system use 1.2 gb for its own use......


> If you installed total 4GB memory, the system will detect less than 4GB of total memory because of address space allocation for other critical functions, such as:

- System BIOS (including motherboard, add-on cards, etc..)
- Motherboards resources
- Memory mapped I/O
- configuration for AGP/PCI-Ex/PCI
- Other memory allocations for PCI devices
 
Different onboard devices and different add-on cards (devices) will result of different total memory size.
e.g. more PCI cards installed will require more memory resources, resulting of less memory free for other uses.

---

### Post by sikander3786 on 2011-02-18
> **MogBug said:**
> I've got an nVidia 8400 GS 256 Mb graphics card but, by the way, the hardware updater doesn't seem to recognise it. (unless in Ubuntu 64 bit it runs as native, which I doubt!)
What is the output of this command.

```
lspci | grep VGA
```

---

### Post by sikander3786 on 2011-02-18
> **PRC09 said:**
> In regards to the memory from the Asus manual........I personally have seen the system use 1.2 gb for its own use......
Might be.... I haven't seen a case like that neither experinced it myself. It would be such a great loss of memory then.

My system just eats up 55MB of RAM as I've got 2 GB.

```

              total       used       free     shared    buffers     cached
Mem:          1945       1115        830          0         85        430

```

---

### Post by CJ_Hudson on 2011-02-18
output is:

04:00.0 VGA compatible controller: nVidia Corporation Device 10c3 (rev a2)

---

### Post by sikander3786 on 2011-02-18
You have connected your monitor to the 256MB one or the motherboard integrated one?

I don't remember many commands to find out more about your graphics card but I doubt if it is your graphics card actually eating up some shared memory. You can look under Bios settings and see how much RAM has been assigned.

---

### Post by CJ_Hudson on 2011-02-18
Thanks, I am honoured by your assistance.
However I cannot get into the BIOS sytem, it remains hopelessly locked despite all my desparately pressing appropriate keys whilst system is booting.

I also do not think my hard drive is properly mounted.

P.S. Sorry monitor is connected by video card

---

### Post by sikander3786 on 2011-02-18
You are most Welcome :-)

> I also do not think my hard drive is properly mounted.

I can try to help with this one. What you mean by the statement? Any error messages or missing partitions or what?

---

### Post by CJ_Hudson on 2011-02-18
There  is a funny "squidge-ing" noise from the hard-drive when the computer reboots.
And an Intel CPU code loading error on the very first splash screen when it boots.
I think I am going to take it back into the shop where I bought it because there is also a problem with Windows on the other partition.

---

### Post by sikander3786 on 2011-02-18
Hard drive noises are not good at all. Most of the time they mean that the drive is failing.

CPU code loading error might go away with a Bios upgrade I think.

If it is in warranty period, it'd be better to get it checked by the professionals.

Hope your issues will be fixed soon.

---

### Post by CJ_Hudson on 2011-02-18
Thankyou sikander3786.

---

### Post by CJ_Hudson on 2011-02-27
Any chance someone could give me a hand getting the video driver for the 8400 Nvidicard working>
I have drawn a blank after extensive reasearch, there seems to be nothing about getting this card working in 64 bit Ubuntu and it doesn't automatically install from -> System -> Administration -> Windows Wireless Drivers?

Sorry to multiple post!

---

