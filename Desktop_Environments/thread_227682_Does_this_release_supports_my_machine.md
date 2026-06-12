---
title: "Does this release supports my machine?"
date: 2006-08-02
forum: Desktop Environments
---

### Post by gurugeek on 2006-08-02
Hello!

I would like to know if the Dapper release supports my machine.

Below are the specs:

Motherboard: ECS NFORCE3-A... (socket 754) 
Processor:  AMD ATHLON 64 3000
Video card: Gforce MX400 NVIDIA...
Display: VIZIO L32 LCD TV

Please I need comments if Ubuntu Dapper will work fine for this specs.

Thank you.

---

### Post by tkjacobsen on 2006-08-02
take a look in the hardware support wiki page: [https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Your motherboaed and processor shouldn't be a problem... And concerning the nvidia card, if you have problems just use the proprietary drivers from nvidia: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by codejunkie on 2006-08-02
> **gurugeek said:**
> Hello!

I would like to know if the Dapper release supports my machine.

Below are the specs:

Motherboard: ECS NFORCE3-A... (socket 754) 
Processor:  AMD ATHLON 64 3000
Video card: Gforce MX400 NVIDIA...
Display: VIZIO L32 LCD TV

Please I need comments if Ubuntu Dapper will work fine for this specs.

Thank you.
i have the same motherboard and a 3400+ cpu nvidia 6200 video card the 32bit version install's and works great, but the 64bit version of ubuntu won't install it keeps locking up at partitioning using the desktop cd, and it locks up at select and install software using the alternate install cd, but the 32bit version works ok.

---

### Post by gurugeek on 2006-08-02
> **codejunkie said:**
> i have the same motherboard and a 3400+ cpu nvidia 6200 video card the 32bit version install's and works great, but the 64bit version of ubuntu won't install it keeps locking up at partitioning using the desktop cd, and it locks up at select and install software using the alternate install cd, but the 32bit version works ok.

I've searched the Ubuntu download page and none tells about AMD32 Ubuntu 6.06 Download.

Thanks anyways, thanks guys for the replies...

BTW will my display work in Ubuntu 6.06?

---

### Post by codejunkie on 2006-08-02
> **gurugeek said:**
> I've searched the Ubuntu download page and none tells about AMD32 Ubuntu 6.06 Download.

Thanks anyways, thanks guys for the replies...

BTW will my display work in Ubuntu 6.06?

it's not listed as AMD32 i was talking about the standard ubuntu install disk  the **PC (Intel x86) desktop CD ** this will install the 32bit version of ubuntu on 32 or 64bit intel and AMD processors.

The 64bit version of ubuntu is called **64-bit PC (AMD64) desktop CD** this version will only work on a 64bit intel and AMD processors not the 32bit ones.
you can find the cd's here [http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

as for your display i don't know for sure, but i assume it should work just fine.
you can check if it is supported though by downloading either of the two cd's i mentioned above.
first make sure the boot order in your bios, is set to boot the cdrom first, then the harddrive. put the cd in and reboot your computer, it will load and run as a live cd, and won't install anything onto your harddrive unless you doubleclick on the install icon on the desktop. this should let you know if it will recongzise your display and your other hardware is supported also before you install.

---

