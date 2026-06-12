---
title: "Memory upgrade"
date: 2009-03-02
forum: General Help
---

### Post by xsilvergs on 2009-03-02
Hi,

I've just installed 4GB ram into my MSI-7176 945G Platinum MB but am not sure it is detected correctly.

Prior to installing the memory I installed the 2.6.27-11-server kernel and typing free -m showed the correct amount of memory.

I then installed the 4 x 1GB sticks, I now get

tony@BlackUbuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2024       1086        937          0         40        580
-/+ buffers/cache:        465       1558
Swap:         2949          0       2949

System Monitor shows under Hardware
Memory: 2.0 GiB

If I sudo lshw -html >> info.html it reports 4 GiB (each of the 4 banks show 1 GiB).

Phoenix Award bios under System show 4GB

Is there something else I need to do?

Thank you.

---

### Post by jespdj on 2009-03-02
Are you using 32-bit or 64-bit Ubuntu?

Note that 32-bit operating systems (Ubuntu, Windows or any other 32-bit operating system) will not be able to address more than about 3.2 to 3.5 GB RAM. The address space of a 32-bit OS is limited to 4 GB, and part of this address space is reserved to communicate with the graphics card and other devices. A 64-bit OS does not have such a limitation.

If you are already running 64-bit Ubuntu and you still have this problem, then look in the BIOS settings of your computer if there is an option named "memory remapping" or something similar, and set it to "enabled". This will move the address space of the graphics card and devices outside the lower 4 GB area, so that the OS can access all the RAM.

If this still doesn't work, there are several possibilities: you have a graphics card that uses the main RAM (it doesn't have its own dedicated video memory), or your PC contains a chipset that doesn't support memory remapping (such as the Intel 945 - which I suspect since your mother board is a MSI-7176 945G).

---

### Post by xsilvergs on 2009-03-02
jespdj

Thanks for replying, I'm running 32-bit.

My graphics card is a GeForce GV-NX72G512P2 7200 GS PCIE Local frame Buffer 256MB DDR2 if that means anything to you (it doesn't mean much to me).

Why does tony@BlackUbuntu:~$ free -m only show 2GiB and info.html show 4GiB?

---

### Post by jespdj on 2009-03-03
The info.html that you generated with lshw shows the real, physical amount of RAM in your system (which is ofcourse 4 GB).

free -m shows how much of that RAM is accessible to the operating system, which is 2.0 GB in your case. The rest of the RAM is reserved for communicating with the graphics card and other devices.

You will not be able to use the full 4 GB, because you are using a 32-bit operating system. Part of the address space has to be used to communicate with the graphics card and other devices. (There are tricks to make a 32-bit OS see up to 64 GB, but it requires a special version of the Linux kernel that supports [PAE](http://en.wikipedia.org/wiki/Physical_Address_Extension)).

---

### Post by xsilvergs on 2009-03-03
jespdj

I upgraded my kernel to Intrepid 2.6.27-11-server just before I installed the memory in preperation as I thought this had PAE and would detect and use all 4GiB.

Should I have installed the memory before the kernel upgrade?

Do I need to do something else to the server kernel I have installed to make it see all 4GiB?

Thanks for your help

---

### Post by xsilvergs on 2009-03-03
All,

Please see memory problem above.

At this moment I'm writting this using the 64bit OS from a CD, when I look at system monitor it says for Memory 2.0GiB.

Considering I have 4G of ram why does it not show it?

---

### Post by oldos2er on 2009-03-03
You shouldn't need to update the kernel. That said, I don't know what's causing your problem, sorry.

---

### Post by Geobot on 2009-03-03
I don't know if this will help, but I had a similar problem going from 1G to 2G of RAM. The system monitor, and everything else OS-related showed 1G while my BIOS(also phoenix) showed the correct 2G. It had me wracking my brain for about two days. 

It started recognizing it completely after I ran a memtest from GRUB one time, having abandoned hope. I don't know if that is what did it or not, but it's the only thing I did differently that time, and it's worked fine since.

Worst that happens is you waste a few minutes on a memory test, right?

---

### Post by xsilvergs on 2009-03-03
Geobot

Have run memtest from Grub afew times on your suggestion but System Monitor still reports Memory: 2.0 GiB. Thanks for suggestion though.

Any one got any other ideas how to get 2.6.27-11-server 32 bit to see 4 GB of memory?

---

### Post by bodhi.zazen on 2009-03-03
> **jespdj said:**
> Note that 32-bit operating systems (Ubuntu, Windows or any other 32-bit operating system) will not be able to address more than about 3.2 to 3.5 GB RAM. The address space of a 32-bit OS is limited to 4 GB, and part of this address space is reserved to communicate with the graphics card and other devices. A 64-bit OS does not have such a limitation.

That information is just wrong.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

PAE allows a 32 bit kernel to access up to 64 Gb RAM

The Ubuntu server kernel is PAE enabled (or you can compile your own).

---

### Post by xsilvergs on 2009-03-03
Is there a way to prove that PAE is enabled?

---

### Post by bodhi.zazen on 2009-03-03
> **xsilvergs said:**
> Is there a way to prove that PAE is enabled?

Look at the kernel config file :

vor : [http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)
        Alternate : [http://ubuntuforums.org/showthread.php?t=853678](http://ubuntuforums.org/showthread.php?t=853678)

---

### Post by xsilvergs on 2009-03-04
In desperation I've install Ubuntu 8.10 64-bit on another HDD

Phoenix-Awardbios reports 4194304k of memory.

tony@BlackUbuntu-64:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2009        535       1473          0         14        184
-/+ buffers/cache:        337       1671
Swap:         1608          0       1608

sudo lshw -html >> info.html it reports 4 GiB (each of the 4 banks show 1 GiB)

Any ideas what I'm doing wrong?

Thanks

---

### Post by xsilvergs on 2009-03-05
Using 64-bit Ubuntu

tony@BlackUbuntu-64:~$ dmesg | head -25
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-11-generic (buildd@crested) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Jan 29 19:28:32 UTC 2009 (Ubuntu 2.6.27-11.27-generic)
[    0.000000] Command line: root=UUID=604f028b-c5aa-475b-a670-46ec876f9875 ro quiet splash 
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfedf800 (usable)
[    0.000000]  BIOS-e820: 00000000cfedf800 - 00000000cfee0000 (reserved)
[    0.000000]  BIOS-e820: 00000000cfee0000 - 00000000cfee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfee3000 - 00000000cfef0000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfef0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0xcfedf max_arch_pfn = 0x3ffffffff
[    0.000000] WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 1278MB of RAM.
[    0.000000] ------------[ cut here ]------------
[    0.000000] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/cpu/mtrr/main.c:1558 mtrr_trim_uncached_memory+0x397/0x3b4()

Apparently this means [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved) it can see 4 GB ram but System Monitor still says I have 2 GiB.

tony@BlackUbuntu-64:~$ cat /proc/mtrr
reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: uncachable, count=1
reg02: base=0xc0000000 (3072MB), size= 256MB: uncachable, count=1
reg03: base=0xcff00000 (3327MB), size=   1MB: uncachable, count=1
reg04: base=0xd0000000 (3328MB), size= 256MB: write-combining, count=1

---

### Post by xsilvergs on 2009-03-10
Well I've done another clean install of Ubuntu 32-bit Desktop on my main HDD and System Manager still reports 2.0 GiB of RAM. 

Now I realise it will not report the 4.0 GiB that installed but can anyone explain where the System Manager gets the RAM size from?

---

### Post by Yellow Pasque on 2009-03-10
You're spinning your wheels trying to get Ubuntu to recognize 4GB if the BIOS/kernel aren't cooperating.
> [ 0.000000] WARNING: BIOS bug: CPU MTRRs don't cover all of memory, losing 1278MB of RAM.

What motherboard/CPU do you have (sudo dmidecode if not sure) and is the BIOS up to date?

---

### Post by xsilvergs on 2009-03-10
Temujin

Thanks for replying with some info.

From memory it's a MSI-7176 945G Platinum MB with an Intel Pentium 4 CPU. The bios was updated only a few months ago.

Is this board one of the boards that that is covered by your warning?

I'm at work at the moment but will dmidecode tonight and post results

---

### Post by Yellow Pasque on 2009-03-10
No need to run dmidecode if you know your motherboard and have the latest BIOS.

Unfortunately, you shouldn't count on it getting fixed any time soon: [http://linux.derkeiler.com/Mailing-Lists/Kernel/2007-06/msg01346.html](http://linux.derkeiler.com/Mailing-Lists/Kernel/2007-06/msg01346.html)

---

### Post by xsilvergs on 2009-03-10
Thanks Temujin, not really the reply I was hoping for but at least it will stop waisting more time on it.

The downer is I spent money on ram which it can't use.

Thanks again.

---

