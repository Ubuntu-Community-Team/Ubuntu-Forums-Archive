---
title: "analyzing a slow system"
date: 2010-09-16
forum: Desktop Environments
---

### Post by deesto on 2010-09-16
I've just installed 10.04-1 64-bit on my system, and while I am pleased with the actual OS so far, I am disappointed to see that the same performance problems I've seen on this system with other OSes persist with Ubuntu.  I wasn't expecting a magic bullet (though just a little magic would be nice!), but at least I know now that most of the problems must be hardware related.  The system often is slow to respond, X GUIs time out often, commands take time to begin executing, etc.

The hardware is a Dell Precision 490 that I've practically gutted to upgrade its disks (RAID1 pair of 1.5 TB disks), memory (6 GB, which are showing up as 5.8 GB, which concerns me a bit), and video (ATI Radeon HD 3600 series); only the CPUs (2 dual-core Xeon 3.20 GHz) and mainboard (last BIOS update: 2008 ) and original CD-R drive remain.

I know the VGA card is purported to support only 2D graphics, and it's currently using proprietary drivers.  It would be nice to get full performance out of it, but I don't think it's the main source of system performance problems.

Launching a new GUI app window sometimes takes several seconds, sometimes many seconds, and sometimes the window appears minutes later, all while there is little or no reported load on the system. The windows also take seconds to disappear after closing.

I am willing to do any or all of the following, but I would like to first verify that they are actual problems before doing them needlessly:
- remove the proprietary ATI drivers and install the open-source version (if the drivers are problematic)
- un-RAID the disks and re-install from scratch (if the RAID is causing performance issues)
- buy a new, fully-supported video card (if the card is causing performance issues)
- something else?

How can I test the above and pinpoint the problems?

---

### Post by deesto on 2010-09-17
> **deesto said:**
> ...
I am willing to do any or all of the following, but I would like to first verify that they are actual problems before doing them needlessly:
- remove the proprietary ATI drivers and install the open-source version (if the drivers are problematic)Tried that; didn't help.
> - un-RAID the disks and re-install from scratch (if the RAID is causing performance issues)Tried that too: deleted the RAID, created new partitions on a single disk, and re-installed Ubuntu.  Didn't help.
> - buy a new, fully-supported video card (if the card is causing performance issues)If the above didn't help, I'm not convinced that buying new hardware will help either.

Any thoughts on how to troubleshoot an unbearably sluggish system, please?

---

### Post by Frogs Hair on 2010-09-17
Two things to investigate , type top in your terminal to see the top processes running and go to Administration > Disk utility and check to see if your hdd is healthy. This may help in your search.

---

### Post by deesto on 2010-09-17
> **Frogs Hair said:**
> Two things to investigate , type top in your terminal to see the top processes running and go to Administration > Disk utility and check to see if your hdd is healthy. This may help in your search.
Thanks.  `top` doesn't show much going on at all, even when windows and commands seem to be frozen.  Usually Firefox is the biggest resource user when running, and that's around a few % of both CPU and memory. Xorg pops up a lot at the top of the CPU list, but even that is just a few % of CPU.

Disk Utility seems fine too.  I've even run some `iozone` tests and those seemed fine.

I had access to an **old** NVIDIA Quadro NVS 285 card, so I've swapped out the ATI Radeon HD 512 MB card for the NVIDIA 128 MB card, and after installing the NVIDIA drivers, I'm already seeing slightly better performance, which to me confirms that something's not right.  So my guesses are still that either the video drivers aren't correct or optimized, or something's wrong with the way memory (video and RAM) is being used by the system.

---

### Post by deesto on 2010-09-21
Does this seem like hardware that should be sluggish?  What can be done to further test and fix it?  
```
$sudo lspci -v
...
07:00.0 VGA compatible controller: nVidia Corporation NV41GL [Quadro FX 1400] (rev a2)
	Subsystem: nVidia Corporation Device 0243
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
	Memory at f0000000 (64-bit, prefetchable) [size=128M]
	Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
	[virtual] Expansion ROM at fce00000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nvidia
	Kernel modules: nvidia-current, nvidiafb, nouveau
...

$cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size=65536MB, count=1: write-back
reg01: base=0x0dff00000 ( 3583MB), size=    1MB, count=1: uncachable
reg02: base=0x0e0000000 ( 3584MB), size=  512MB, count=1: uncachable
reg03: base=0xff0000000 (65280MB), size=  256MB, count=1: uncachable

$cat /proc/meminfo 
MemTotal:        6124164 kB
MemFree:         2793732 kB
Buffers:           79448 kB
Cached:          1446668 kB
SwapCached:            0 kB
Active:          2032572 kB
Inactive:         909820 kB
Active(anon):    1423276 kB
Inactive(anon):      112 kB
Active(file):     609296 kB
Inactive(file):   909708 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:      14291952 kB
SwapFree:       14291952 kB
Dirty:               948 kB
Writeback:           132 kB
AnonPages:       1416320 kB
Mapped:           171100 kB
Shmem:              7136 kB
Slab:             146600 kB
SReclaimable:     125548 kB
SUnreclaim:        21052 kB
KernelStack:        2968 kB
PageTables:        26564 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    17354032 kB
Committed_AS:    2221660 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      343400 kB
VmallocChunk:   34359388148 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      692264 kB
DirectMap2M:     5597184 kB

$cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Xeon(TM) CPU 3.20GHz
stepping	: 4
cpu MHz		: 3191.925
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl vmx cid cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 6383.85
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Xeon(TM) CPU 3.20GHz
stepping	: 4
cpu MHz		: 3191.925
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl vmx cid cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 6383.80
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Xeon(TM) CPU 3.20GHz
stepping	: 4
cpu MHz		: 3191.925
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl vmx cid cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 6383.75
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 15
model		: 6
model name	: Intel(R) Xeon(TM) CPU 3.20GHz
stepping	: 4
cpu MHz		: 3191.925
cache size	: 2048 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 6
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc pebs bts pni dtes64 monitor ds_cpl vmx cid cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 6383.77
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 48 bits virtual
power management:

$ uname -a
Linux mymachine 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
```

---

### Post by deesto on 2010-10-27
The only additional clue I can find are constant entries in the system log about USB device speed resets, which show up consistently in intervals between 2 and 30 minutes:
```
Oct 27 08:49:34 myhost kernel: [73742.061904] usb 4-2: reset low speed USB device using uhci_hcd and address 3

```

---

### Post by 3Miro on 2010-10-27
When it was still on its own, ATi had virtually no Linux support. When AMD came by, they made huge improvements, however, their natural priority is the newer cards. Basically any Radeon 3xxx is poorly supported by any driver. NVIDIA on the other hand does support old and new cards, it is just that some of them are really old in terms of hardware.

Have you tried disabling the graphical effects. If things improve, then you know where the problem is, if they don't improve, then you know where it is not.

---

### Post by deesto on 2010-10-27
Hi 3Miro,> **3Miro said:**
> Have you tried disabling the graphical effects. If things improve, then you know where the problem is, if they don't improve, then you know where it is not.Yes, I have: desktop effects are disabled on my system, and, unfortunately, the setting has no bearing on the issue.  It's been very frustrating (to say the least) to troubleshoot the problem, not to mention to communicate to Dell that a problem exists.

---

### Post by 3Miro on 2010-10-27
If the visual effects are off, then the video is not an issue here. 

From reading your previous posts, I have a hard time understanding what exactly is the problem. Can you be specific on what is it in your system that doesn't work the way you want it. Do applications take too long to open or are they sluggish afterwards. What applications are we talking about and so on.

---

### Post by deesto on 2010-10-28
Yeah: I realize the problem seems vague, but it's tough to qualify when I don't know the cause.  I tried to explain in the first post:
> Launching a new GUI app window sometimes takes several seconds, sometimes many seconds, and sometimes the window appears minutes later, all while there is little or no reported load on the system. The windows also take seconds to disappear after closing.


To try and expand on that, just about everything is slow to respond: if I click a menu item, it sometimes takes seconds to display its sub-menu; if I open a new application, it either pops up instantly, or it can take seconds to minutes to appear (I've literally had windows pop up 5 or more minutes after I'd clicked on them to open).  When browsing with Firefox, clicking a page, or typing in the search bar, sometimes takes several seconds to respond or even show what I've cicked or typed; sometimes even terminal commands don't appear as I type or take a while to send back results.  Once in a while, there's no delay at all, but this is rare.

---

### Post by 3Miro on 2010-10-28
This is very puzzling ... 

My first guess on something like this would be the Video card (I have seen things like that on a video card with bad ATI driver), however, if this is happening with no visual effects enabled, then I don't know.

I have seen something like this when I use sshfs with slow internet connections, file managers tend to become very slow even when they work on local files and folders. However, your problem is across the entire system.

Since the problem exists on other OS as well, it may be hardware related. If everything is ultimately working just very slow, then you may have issues with the motherboard. You can try looking for specific information on it and maybe you will find some troubleshooting info from the manufacturer/manufacturer's forum.

Other than that, there is only one thing that I can think of. If terminal commands are slow without seeing heavy CPU usage by a rouge process, then you can shutdown the graphical environment altogether. I think you can do that with Ctr + Alt + F1 or F2, Ctr + Alt + F7 should get you back to the graphics. Test to see if terminal commands are slow even without any graphics.

---

### Post by deesto on 2010-10-28
Hi 3Miro,> **3Miro said:**
> This is very puzzling ... 

My first guess on something like this would be the Video card (I have seen things like that on a video card with bad ATI driver), however, if this is happening with no visual effects enabled, then I don't know.

I have seen something like this when I use sshfs with slow internet connections, file managers tend to become very slow even when they work on local files and folders. However, your problem is across the entire system.Right.  I'm not using sshfs.

> Since the problem exists on other OS as well, it may be hardware related. If everything is ultimately working just very slow, then you may have issues with the motherboard. You can try looking for specific information on it and maybe you will find some troubleshooting info from the manufacturer/manufacturer's forum.Yeah, I've tried this and found very little, except that these machines seem to have an MTTR problem, which the manufacturer denies.

> Other than that, there is only one thing that I can think of. If terminal commands are slow without seeing heavy CPU usage by a rouge process, then you can shutdown the graphical environment altogether. I think you can do that with Ctr + Alt + F1 or F2, Ctr + Alt + F7 should get you back to the graphics. Test to see if terminal commands are slow even without any graphics.Yep: same delays in command response in console mode, lower init levels, even in su mode.

---

### Post by deesto on 2010-11-05
I officially give up on this system.  I've spent years trying to make sense of it.  Dell's solution was to point me to instructions in a blog post on installing proprietary NVIDIA drivers (and play it off as their own procedure).

My advice: if you[re using *NIX, do **not** bother with a Dell Precision 490.

---

