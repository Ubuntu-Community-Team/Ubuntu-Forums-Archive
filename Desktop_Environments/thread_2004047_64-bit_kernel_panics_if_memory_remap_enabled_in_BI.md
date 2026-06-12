---
title: "64-bit kernel panics if memory remap enabled in BIOS"
date: 2012-06-15
forum: Desktop Environments
---

### Post by leo_m on 2012-06-15
I have total 6 GB of RAM installed.

Ubuntu 12.04 64-bit flavours refuse to install with a kernel panic indicating hardware failure if I enable memory remap in BIOS (which led me to change the memory module, luckily I happened to have a spare one lying around).  If I disable the memory map in BIOS, installation proceeds smoothly but the operating system is only able to use 3 GB (as indicated by free -g).

The motivation behind installing 64-bit was to be able to use 6GB - I already had 32-bit flavours of Ubuntu and of Windows 7 running without any problem (and they continue to run without problem irrespective of whether memory remap is enabled in BIOS).

Please help me in using the whole 6GB in 64-bit install...

---

### Post by sanderj on 2012-06-15
Interesting ...

Does the panic happen at boot, or at some moment after booting?

I would do this:
- run memtest86 (it is in the GRUB boot menu) for a few hours to really test your memory
- try 32-bit Ubuntu 12.04. As the recent Ubuntu versions use the PAE kernel, it will use all memory (6GB in your case)

---

### Post by leo_m on 2012-06-15
I installed 64-bit because 32-bit OS was not using the full 6 GB...(the latest ubuntu 12.04 that is).  Specifically, I used ubuntu business remix 12.04 32-bit.

Ubuntu, Ubuntu Studio, Xubuntu all give the same error upon memory remapping enabled.  The error is shown at boot time itself.  Now that I have disabled the remapping, I have been able to install and have been using the computer non-stop for several hours post-install without any issues (except the main issue that I am not able to use all 6 GB)

I shall leave memtest running overnight and post the findings.

---

### Post by sanderj on 2012-06-15
Memtest running: with the memory remapping enabled, right?


Ubuntu 32-bit can show & use more than 3.5 GB, as long as you have installed the PAE-kernel. I thought the Ubuntu installer would do that automatically. If not, you can post-install it.

You can my script to get all info on your memory: BIOS, CPU, OS, PAE, etc:

```
wget http://www.appelboor.com/dump/check-my-hardware.py
python check-my-hardware.py
```

HTH

---

### Post by leo_m on 2012-06-21
I shall try your script later tonight.

memtest offers so many options! it ran fine with the default options selected and remapping enabled in BIOS.  But it fails when I select some of the options in memtest (can't recollect which, will try again).

Windows 7 memtest succeeds with memory remapping enabled in BIOS.  Windows PAE forced mode does not result in more than 4G being recognized either.

Both Ubuntu and Win7 are behaving consistently: both refuse to allow me usage of more than 4GB, both have memtest succeeding with default options and memory remapping enabled in BIOS.

[edit: the 4GB RAM DIMM is [FONT=monospace]Kingston Value RAM KVR1333D3N9/4G / 4GB / PC3-10600 / 1333MHz / DDR3 / 240 Pin / CL9 / Unbuffered DIMM[/FONT]]

I don't know what speed the two DIMMs (one 4GB, the other 2 GB) are actually running at: the BIOS doesn't help me in that regard, let alone allowing me to adjust the speed, it does allow me to adjust latency, but if I tinker there, the system either doesn't boot (blank screen, no errors) or reboots.  Every time I disable and re-enable memory remapping in BIOS, the first time Ubuntu reboots in the middle of boot-up, the second time onwards throws kernel panic.

[edit: the latency I was talking about in above para is PCI latency, not RAM latency, sorry for that]

---

### Post by leo_m on 2012-06-21
> You can my script to get all info on your memory: BIOS, CPU, OS, PAE, etc:The output is as expected:

check-my-hardware.py - version: SJ 2012-06-03
OK, you're root
ANALYSIS:
Total of physical memory modules found 6144 MB in 2 memory module(s)
BIOS offers 3318 MB as usable
Memory seen by OS 3261 MB
BIOS version 06/10/2010
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 2826 MB
Memory difference between BIOS offering and memory seen by OS 57 MB
Memory difference between DIMM hardware and memory seen by OS 2883 MB

ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole rempapping / hoisting' in your BIOS to get more usable memory

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 6GiB
          description: DIMM SDRAM Synchronous
          size: 4GiB
description: DIMM SDRAM Synchronous
          size: 2GiB

Finished

The 4GB DIMM is            Kingston Value RAM KVR1333D3N9/4G / 4GB / PC3-10600 / 1333MHz / DDR3 / 240 Pin / CL9 / Unbuffered DIMM

I don't know what to do - enabling memory remapping will result in Ubuntu not booting up...

The max. supported memory for the computer is 8GB as per the specs. on the manufacturer's website...

---

### Post by hawkmage on 2012-06-22
Are you by any chance running an ATI video card and using an ATI provided video driver?  There are many of the ATI drivers that make the assumption that the video memory addresses are linear and not remapped.  So when you turn on remapping the driver has no idea what is going on and trashes memory.  

This is not a Linux specific issue.

---

### Post by leo_m on 2012-06-22
ATI Radeon HD 5450.

Time to switch back to Ubuntu default non-proprietary driver?

[update] Uninstalled proprietary ATI fglrx driver to no avail.  The problems remain.  If I set the memory remapping, prior to kernel panic, I get an ATA error (HDIO, unable to identify /dev/sdc; or similar error).  I don't know why that error comes up.

I am now thinking the error could be due to incompatible (with each other) RAM DIMMs?

The 4 GB DIMM is: Kingston Value RAM KVR1333D3N9/4G / 4GB / PC3-10600 / 1333MHz / DDR3 / 240 Pin / CL9 / Unbuffered
The 2 GB DIMM is: Elixir 2GB DDR3 PC3-10600 (M2Y2G64CB8HC5N-CG)

Can someone confirm if they are compatible with each other or not?

[edit: looks like both are 1333 MHz, 240-pin, CL9 latency, PC3-10600 DDR3 RAM modules, so should not be incompatible]

---

### Post by leo_m on 2012-06-23
Made some progress.   It could be the SATA controller.  The SATA controller has 3 modes: AHCI, IDE and RAID.  For modes other than IDE, Ubuntu boot-up fails with kernel panic when memory remapping is enabled.  For mode IDE, if memory remapping is enabled, I get the ATA idenfity error I alluded to earlier ( HDIO, unable to identify /dev/sdc; or similar error), but the computer boots up and free -m as well as the python script provided by sanderj report all of 6GB available:
-----
./check-my-hardware.py - version: SJ 2012-06-03
OK, you're root
ANALYSIS:
Total of physical memory modules found 6144 MB in 2 memory module(s)
BIOS offers 6134 MB as usable
Memory seen by OS 5975 MB
BIOS version 06/10/2010
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 10 MB
Memory difference between BIOS offering and memory seen by OS 159 MB
Memory difference between DIMM hardware and memory seen by OS 169 MB

ADVICE:
Nothong unusual found, so no advice for your setup

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 6GiB
          description: DIMM SDRAM Synchronous
          size: 4GiB
          description: DIMM SDRAM Synchronous
          size: 2GiB

Finished
-----

I also ran memtest+ in standard test mode overnight (again) and it reported everything normal (no errors), except that in one of its reporting screens, it could not report the size of the 4GB DIMM (various screenshots attached).  I do not know if that is significant.

My next course of action should be to contact the computer vendor and try to get a BIOS update then - do you think that will fix the SATA controller issue ?

---

### Post by techvish81 on 2012-06-23
a bios update can sometimes be more problematic than the problem itself, so i think you should read changelog or any such thing from the vendors website to confirm whether it could solve your problem or has nothing related to your problem. if later is true,  better to leave it as it is and run in ide sata controller mode to get all the ram available

---

### Post by leo_m on 2012-06-23
> better to leave it as it is and run in ide sata controller mode to get all the ram available

I would have done that compromise (actually wanted to use the SATA RAID option, not AHCI, but the computer fails with RAID too, same/similar error), except for the fact that with IDE, the computer crashes unpredictably on disk read-write.

Is there a way to be able to use all of the RAM?

---

