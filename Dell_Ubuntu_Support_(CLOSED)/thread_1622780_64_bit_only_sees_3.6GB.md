---
title: "64 bit only sees 3.6GB"
date: 2010-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by UncleBoarder on 2010-11-15
I installed 64bit Ubuntu (10.04.1) about 2 months ago and have been running 4GB (3.6 showing) without any problems.  Tonight I upgraded to 6GB, it runs fine, but Ubuntu still shows 3.6.

BIOS shows 6GB

Live CD (64bit) shows 3.6

Dell XPS 400.

I have no idea what's going on.  I've read about 20 threads on memory and it all has to do with either the BIOS not reporting the memory accurately or people running 32bit.  I have neither of those issues.

> ed@ubuntu:~$ uname -m
x86_64
ed@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       3606652    1212596    2394056          0      29168     293468
-/+ buffers/cache:     889960    2716692
Swap:      1648632          0    1648632Help please.

---

### Post by skooternb on 2010-11-15
But does your BIOs think you are running 32 bit?

---

### Post by UncleBoarder on 2010-11-15
Well... would my BIOS show 6GB available if it didn't?

---

### Post by PRC09 on 2010-11-16
The spec for your machine according to the Dell website is:

```
512 MB dual channel DDR2-533MHz SDRAM standard, upgradable to 4 GB1 dual channel DDR2-667MHz SDRAM
4 DIMM slots

```
Your bios may see it but apparently only 4gb is accessible....


[http://www.dell.com/us/en/dfb/desktops/xps_400/pd.aspx?refid=xps_400&cs=28&s=dfb](http://www.dell.com/us/en/dfb/desktops/xps_400/pd.aspx?refid=xps_400&cs=28&s=dfb)

---

### Post by skooternb on 2010-11-16
Sorry I wasn't more clear!  32 bit systems can only 'access' up to 4g of memory, so that is the issue.  Make sure you install 64 bit ubuntu.

---

### Post by UncleBoarder on 2010-11-16
Yes, but Dell's site doesn't reference using a 64-bit OS.  And I did research before purchasing, I've found sites that state 4GB max and sites that state 8GB max with 64-bit OS.

I realize this might be a hardware problem but it seems other people have accomplished it.  How can I be certain this isn't something I can fix?

It seems encouraging that the BIOS sees 6GB, is there some test I can run that shows the capability of the chipset?

---

### Post by gibbylinks on 2010-11-16
> **PRC09 said:**
> The spec for your machine according to the Dell website is:

```
512 MB dual channel DDR2-533MHz SDRAM standard, upgradable to 4 GB1 dual channel DDR2-667MHz SDRAM
4 DIMM slots

```Your bios may see it but apparently only 4gb is accessible....


[http://www.dell.com/us/en/dfb/desktops/xps_400/pd.aspx?refid=xps_400&cs=28&s=dfb](http://www.dell.com/us/en/dfb/desktops/xps_400/pd.aspx?refid=xps_400&cs=28&s=dfb)

As far as this post goes, Dell say my Inspiron 1501 can only run 2gb max and yet I'm happily using 4gb and I'm not the only one on these forums with 4gb on this laptop. I take what Dell say as a guideline, but not gospel...I mean they only designed the machines :mrgreen:

---

### Post by PRC09 on 2010-11-16
I found this article on a windows site that was dealing with the same issue.Not sure if it is applicable to Ubuntu but it seems to be a hardware/bios issue....  


 >  * The chipset must support at least 8 GB of address space. 
    * The CPU must support the x64 instruction set. The AMD64 CPU and the Intel EM64T CPU support this instruction set.
    * The BIOS must support the memory remapping feature. The memory remapping feature allows for the segment of system memory that was previously overwritten by the Peripheral Component Interconnect (PCI) configuration space to be remapped above the 4 GB address line. This feature must be enabled in the BIOS configuration utility on the computer. View your computer product documentation for instructions that explain how to enable this feature. Many consumer-oriented computers may not support the memory remapping feature. No standard terminology is used in documentation or in BIOS configuration utilities for this feature. Therefore, you may have to read the descriptions of the various BIOS configuration settings that are available to determine whether any of the settings enable the memory remapping feature.
    
Contact the computer vendor to determine whether your computer meets these requirements.

Note: When the physical RAM that is installed on a computer equals the address space that is supported by the chipset, the total system memory that is available to the operating system is always less than the physical RAM that is installed. For example, consider a computer that has an Intel 975X chipset that supports 8 GB of address space. If you install 8 GB of RAM, the system memory that is available to the operating system will be reduced by the PCI configuration requirements. In this scenario, PCI configuration requirements reduce the memory that is available to the operating system by an amount that is between approximately 200 MB and approximately 1 GB. The reduction depends on the configuration.

---

### Post by UncleBoarder on 2011-03-12
I've given up.  I no longer believe my chipset is capable of more than 4GB.

Thanks everyone.

---

