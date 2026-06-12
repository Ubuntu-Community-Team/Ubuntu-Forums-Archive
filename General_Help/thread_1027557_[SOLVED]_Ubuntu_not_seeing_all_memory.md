---
title: "[SOLVED] Ubuntu not seeing all memory"
date: 2009-01-01
forum: General Help
---

### Post by ricardo_78 on 2009-01-01
Hi i am a noob so go easy.

Just getting to grips with Ubuntu and pretty impressed. 

I have loaded Xubuntu desktop package on my Ubuntu Server... However the desktop is pretty slow.....I looked at System Monitor and note that it only sees 82 MiB of memory ie mem usage is correspondingly high....  I have ~1 GB of RAM installed.... 

I previously downloaded ubuntu-desktop however that was even slower...

Can my old video card be grabbing all that memory?

Can I fix it in software or spend a few quid on a new card?

Any pointers would be well received...

---

### Post by sdennie on 2009-01-01
Can you post the output of:

```

free -m

```

---

### Post by lensman3 on 2009-01-01
What does the "free" command say?

Linux reports free memory on the system and it is different that what is reported by M$'s XP/Vista.  Most of the time in Linux, the unused ram is used by the file system to cache info from the disk so that data can be accessed faster. 

See what the size of /proc/kcore file is.  The is a pseudo file that maps used system memory into the user address space. (Don't try to remove this file, it is not really there).  I have a 4Gb-ram, 64bit system and kcore is 4.8 Gig in size.   

You also might run the command, from text screen: "dmesg | more".  Look at the first parts of this file.  It should also report how much memory the kernel sees and uses.

---

### Post by albinootje on 2009-01-01
> **vor said:**
> Can you post the output of:

```

free -m

```

Can you, ricardo_78, also post the output of :
```

cat /proc/cpuinfo
cat /proc/meminfo
dmesg |grep -i mem

```
And the brand name and type of your computer.
Or if it's a self build computer the name+type of BIOS.

---

### Post by ricardo_78 on 2009-01-01
the free -m creates the following:


richard@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:            82         80          2          0          0         14
-/+ buffers/cache:         65         17
Swap:          462        179        283


cat proc/meminfo gives:

Writeback:           0 kB
AnonPages:       43464 kB
Mapped:          11684 kB
Slab:            10160 kB
SReclaimable:     2744 kB
SUnreclaim:       7416 kB
PageTables:       1932 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:    516020 kB
Committed_AS:   330148 kB
VmallocTotal:   937976 kB
VmallocUsed:      3764 kB
VmallocChunk:   934060 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     4096 kB
DirectMap4k:     16320 kB
DirectMap4M:     73728 kB

---

### Post by ricardo_78 on 2009-01-01
my computer is an old noname box.....Bios Award 2A5LHF0A 

Looking at the stuff below appears the Bios is not mapping all the memory...is that correct?

Dangerous thing curiosity combined with a lack of knowledge :D

richard@ubuntu:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-9-generic (buildd@rothera) (gcc version 4.3.
2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 21:57:00 UTC 2008 (Ubuntu 2.6.27-
9.19-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000057f0000 (usable)
[    0.000000]  BIOS-e820: 00000000057f0000 - 00000000057f3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000057f3000 - 0000000005800000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x57f0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 57f0000 @ 7000-d000

---

### Post by sdennie on 2009-01-01
That's a good theory.  To test it, reboot your machine with acpi=off.  Instructions on doing that can be found here: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ricardo_78 on 2009-01-02
I have tried to turn acpi=off by updating /boot/grub/menu.lst as suggested but still can only see 82.3 MiB of system memory. 

Checked that menu.lst has been updated....and looked at DMESG again.  Still have the ref to acpi as per previous post.  

Pretty impressive that this is running at all in the memory, so I will plod on....

Thanks for the help so far...

---

### Post by albinootje on 2009-01-02
Can you try with the mem= boot parameter ?

See here :
[http://www.linux-mips.org/archives/linux-mips/2007-03/msg00477.html](http://www.linux-mips.org/archives/linux-mips/2007-03/msg00477.html)

It's weird that you would need that, because it's several years ago I saw people needing it for their machines.

Did you check your BIOS settings ?
Could it possibly have to do with this "OS/2 64 Mb gap" BIOS option ?

---

### Post by ricardo_78 on 2009-01-02
albinootje:

Ref: the "OS/2 64 Mb gap" BIOS option 

Not sure ...I have selected non-os2....

I have played with setting mem= but again cant see all memory.

I have dug out a bot more memory ... I know have 512MB of RAM but can only see 155648Kb  (Apologies: I was wrong about how much I initially had in the machine)

Guess I need to read some more :D

---

### Post by albinootje on 2009-01-02
> **ricardo_78 said:**
>  I have dug out a bot more memory ... I know have 512MB of RAM but can only see 155648Kb  (Apologies: I was wrong about how much I initially had in the machine)


Are you able to use the full amount of the 512 Mb of RAM with some other OS ?

Is this an fairly old machine ?
I've seen a 256 Mb RAM module which was recognized as 64 Mb in some machines.

How many RAM modules are you using ?
128 Mb + 32 Mb kind of makes the 155658 Kb you mentioned.

---

### Post by ricardo_78 on 2009-01-02
I am using 256 x 2...

Its an old machine that my father had.  Found out that the Bios is Proprietary OEM Version (Time Computers)...

Maybe time to give into this and consider getting a cheap motherboard.....

Thanks for working this through with me.  

Great community!!

---

### Post by ricardo_78 on 2009-01-03
I marked this thread as solved as I believe that its old hardware memory/compatibility problems.

I decided to give the operating system a chance. :)  I have seen enough I am a convert and I am converting!!!

Many thanks for all that helped me along this learning curve...

---

### Post by albinootje on 2009-01-03
> **ricardo_78 said:**
> I marked this thread as solved as I believe that its old hardware memory/compatibility problems.

I decided to give the operating system a chance. :)  I have seen enough I am a convert and I am converting!!!

Many thanks for all that helped me along this learning curve...

Nice to read this.
Have fun with Linux now and in the future! :D

---

