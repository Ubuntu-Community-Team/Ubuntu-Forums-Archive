---
title: "IOMMU boot settings"
date: 2009-02-05
forum: General Help
---

### Post by screaminfakah on 2009-02-05
Hello,
I installed more ram on my pc and now Ubuntu will not let me connect to the internet and doesn't detect my onboard audio.
From extensive searching on the forums and Google this is a problem with the AGP Aperture settings in the kernel.
I tried adding  "iommu=noaperture" , "iommu=noagp", "iommu=memaper=1"  , "iommu=memaper=2" , "iommu=memeaper=3"  
in seperate attempts to the grub boot menu with no fix to my problem.  I still get the aperture error message upon booting.
There is no settings in my bios either and no bios updates available.

I am running Ubuntu 8.10 64 bit
I have 4 gigs ram
System chipset is AMD 690V + SB600
Bios is Phoenix 6.00pg

Does anyone know of another fix other than what I have tried?

I really like Linux and would hate be stuck with Windows.
Thanks

---

### Post by dcstar on 2009-02-05
> **screaminfakah said:**
> Hello,
I installed more ram on my pc and now Ubuntu will not let me connect to the internet and doesn't detect my onboard audio.
From extensive searching on the forums and Google this is a problem with the AGP Aperture settings in the kernel.
I tried adding  "iommu=noaperture" , "iommu=noagp", "iommu=memaper=1"  , "iommu=memaper=2" , "iommu=memeaper=3"  
in seperate attempts to the grub boot menu with no fix to my problem.  I still get the aperture error message upon booting.
There is no settings in my bios either and no bios updates available.

I am running Ubuntu 8.10 64 bit
I have 4 gigs ram
System chipset is AMD 690V + SB600
Bios is Phoenix 6.00pg

Does anyone know of another fix other than what I have tried?

I really like Linux and would hate be stuck with Windows.
Thanks

The message appears on PCI-E systems with 4G+ ram and should not matter because PCI-E systems do **not** have AGP hardware and therefore should not need/use an AGP Aperture.

If you have other issues I would recommend resetting your BIOS so any hardware devices are then mapped above your new RAM - or it could be that there is a problem with the new RAM.

---

### Post by screaminfakah on 2009-02-06
The Linux Kernel is built to look for agp aperture regardless if it is hardware detected.  The problem lies with the X86-64 architecture and the way is addresses the memory.  AMD uses IOMMU settings and Intel uses something a bit different.
I have found no options for remapping the ram and no options for IOMMU or GART settings in my bios.  There is no update for the bios from the OEM as well.  (Acer blows and sucks at the same time....... Its like a paradox!)  

Well until I can upgrade my motherboard and build a new pc,
looks like it will be Windows for me.:(


I just don't understand how this has not been fixed in the Kernel by default since it has been an issue with many people since 2006.  Who in hell even uses AGP anymore???

---

