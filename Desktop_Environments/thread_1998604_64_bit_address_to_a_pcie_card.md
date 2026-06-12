---
title: "64 bit address to a pcie card"
date: 2012-06-07
forum: Desktop Environments
---

### Post by flyingbee on 2012-06-07
Hi,
I have a 64 bit PCIe card that is connected to 64 bit PC running ubuntu (**Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux**).  Linux enumerate this PCIe card and assign 64 bit addresses to 64 bit BARS.

Problem is that higher 4 bytes of these addresses are zero, even if they are 64 bit address 
they lies in 32 bit range.

Is it somehow possible to assign real 64 bit addresses ?

This is lspci output on my ubuntu PC.

    Region 0: Memory at fddff000 (64-bit, non-prefetchable) [size=4K]
    Region 2: Memory at fd000000 (64-bit, prefetchable) [size=8M]
    Region 4: Memory at fc800000 (64-bit, prefetchable) [size=8M]

Regards,
Flyingbee.

---

### Post by flyingbee on 2012-07-03
Hi,
Is there any suggestion for the above problem ?
I have already tried to push address in real 64 bit range by asking resource size up to 1GB/2GB.
but either system allocates size from 32 bit range or fails if unable to get size from 32 bit range addresses.

Any Suggestion?

Regards,
Flyingbee.

---

### Post by 3Miro on 2012-07-03
I don't understand your problem. All video cards are 32-bit devices, they only support up to 4GB of memory.On a 64-bit machine, the video RAM is assigned to be the lower range so that the video card can address it, while the upper range is given to the 64-bit CPU. Older motherboards had a special setting to do that in the BIOS, newer ones do this automatically.

Basically, a video card can use only 32-bit addresses.

---

### Post by flyingbee on 2012-07-04
Hi,

My device is not a video card, its a simple pcie card and according to pcie specs a card can ask for resources(memory for BARS) from system. if a card ask resource for it's BAR that can not be fulfilled from lower 4GB address range then system must should fulfill this request from addresses space above 4GB using higher address in 64 bit range.

Regards,
Flyingbee.

---

### Post by aidan.dixon on 2012-07-31
Hi, Flyingbee

The answer to your question is not actually so obvious.

Although the hardware you have does indeed have 64-bit BARs (two adjacent 32-bit BARs joined together) the BIOS will not necessarily assign an address in 64-bit space.  It usually won't by default because it cannot assume that the OS that boots is capable of accessing PCI memory mapped above 4GB.  Obviously, a 32-bit OS is limited to 32-bit space and so PCI-mapped memory above 0xffffffff would be unusable.

Note that it is normally the BIOS (or UEFI) that assigns addresses to memory behind PCI devices.  This is because the BIOS usually knows the most specific things about platform configuration that enable it to do that.  The OS usually expects to find PCI devices (and the PCI bridges behind which they sit) fully configured these days.

I do not see this policy (setting 32-bit addresses for 64-bit BARs) changing until the penetration of UEFI (instead of traditional BIOS) without 16-bit compatibility (MBR-based partitioning and all) is much more widespread.  This is starting to happen now (Windows 8 will be UEFI only, I believe) and there are Linux builds that are intended for UEFI and GPT-partitioned disks with no 16-bit boot loader code.

If you have installed a 64-bit OS on GPT disks then maybe see if your BIOS is 64-bit and, if so, whether this is a switch to enable/disable 16-bit compatibility.  On AMI APTIO (UEFI) based systems this is called CSM or CSM16 (compatibility support module) and sometimes this can be disabled in the setup menu. Maybe that would be enough to let it assign full 64-bit addresses.

Regarding graphics cards, if a graphics card had even 1GB of memory, then it'd be real bummer for a system in 32-bit mode if all that memory had to be mapped in one chunk into 32-bit memory space.  The graphics card would take up 1/4 of the whole systems memory space and seriousl reduce the space left for system RAM.  I am not sure how they do it.

I do not see anythingn to stop a graphics card having an internal 64-bit architecture and 64-bit PCI base address registers, which are a standard part of the PCIe specification.

-a.

---

