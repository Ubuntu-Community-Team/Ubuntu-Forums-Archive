---
title: "Screen tearing/White boxes left behind windows."
date: 2015-09-28
forum: Desktop Environments
---

### Post by Aberts10 on 2015-09-28
I'm using the Latest Lubuntu, on a oldish Inspiron 1464 laptop, After using it for a while occasionally It may start showing white boxes left behind Windows and applications, Ive noticed it a lot with Firefox which will stop responding and ill have to kill it and wait for the gui to respond... Could it be overheating? Software? Faulty hardware?, I've had lots of problems including overheating in the past, Windows slowed to a crawl, Ubuntu's Gui Freezing up and nothing showing but orange and white squares and lots of crash reports, Dell has made me reinstall Windows 7 almost one hundred times already, And use the BIOS tool that checks the hardware, which always comes out with nothing detected. But I don't think its software because ive tried 10 Linux and 2 window installations and they all have a issue of slowness, GUI, or Crash reports.

---

### Post by ajgreeny on 2015-09-28
More info needed please about the hardware in that "oldish Inspiron 1464 laptop".

What graphic card does it have?  Let's see the output of the terminal command ```
lspci | grep VGA
```

How much memory (RAM) does it have?  What CPU?

---

### Post by Aberts10 on 2015-10-02
Inspiron-1464:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

-Processors-
Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz        : 933.00MHz
Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz        : 933.00MHz
Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz        : 933.00MHz
Intel(R) Core(TM) i3 CPU       M 350  @ 2.27GHz        : 933.00MHz

Ram 4GB DDR3:

-Memory-
Total Memory        : 3841188 kB
Free Memory        : 2853520 kB
MemAvailable        : 3088080 kB
Buffers        : 54800 kB
Cached        : 433388 kB
Cached Swap        : 0 kB
Active        : 548776 kB
Inactive        : 332332 kB
Active(anon)        : 393904 kB
Inactive(anon)        : 96748 kB
Active(file)        : 154872 kB
Inactive(file)        : 235584 kB
Unevictable        : 32 kB
Mlocked        : 32 kB
Virtual Memory        : 3981308 kB
Free Virtual Memory        : 3981308 kB
Dirty        : 352 kB
Writeback        : 0 kB
AnonPages        : 392956 kB
Mapped        : 221588 kB
Shmem        : 97728 kB
Slab        : 46824 kB
SReclaimable        : 26080 kB
SUnreclaim        : 20744 kB
KernelStack        : 5056 kB
PageTables        : 15684 kB
NFS_Unstable        : 0 kB
Bounce        : 0 kB
WritebackTmp        : 0 kB
CommitLimit        : 5901900 kB
Committed_AS        : 1996488 kB
VmallocTotal        : 34359738367 kB
VmallocUsed        : 544884 kB
VmallocChunk        : 34359177180 kB
HardwareCorrupted        : 0 kB
AnonHugePages        : 96256 kB
CmaTotal        : 0 kB
CmaFree        : 0 kB
HugePages_Total        : 0
HugePages_Free        : 0
HugePages_Rsvd        : 0
HugePages_Surp        : 0
Hugepagesize        : 2048 kB
DirectMap4k        : 109484 kB
DirectMap2M        : 3876864 kB

---

### Post by ajgreeny on 2015-10-03
That is surprising; generally Intel graphics are very well supported except for the very latest versions, which take a while to be covered by the xorg drivers.  Your system, however is not one of the most recent Intel chips so I would expect it to be fine.

You say you are using the latest version of Ubuntu but which actual version is it, 14.04, 15.04, or even 15.10 which is not yet fully released?

---

### Post by Aberts10 on 2015-10-09
-Version-
Kernel        : Linux 3.19.0-28-generic (x86_64)
Compiled        : #30-Ubuntu SMP Mon Aug 31 15:52:51 UTC 2015
C Library        : Unknown
Default C Compiler        : GNU C Compiler version 4.9.2 (Ubuntu 4.9.2-10ubuntu13) 
Distribution        : Ubuntu 15.04
-Current Session-
Computer Name        : Inspiron-1464
Home Directory        : /home/user
Desktop Environment        : LXDE (Lubuntu)
-Misc-
Uptime        : 7 minutes
Load Average        : 0.30, 0.42, 0.28


Its not that new? Has intel stopped making chips? this computers about 3 1/2 years old now

Edit: i misread you reply. I though you said that its a newer chip.

---

### Post by meltingpot2015 on 2016-01-03
Try installing the latest Intel (propriety) driver. That driver will most probably have a setting to prevent screen tearing. Of course, if you set it, it does this at the cost of performance. But if you use the correct (latest) driver, you may never have to enable the setting.

---

### Post by deadflowr on 2016-01-04
> **meltingpot2015 said:**
> Try installing the latest Intel (propriety) driver. 
No such thing.
While intel provides newer drivers, all intel drivers are open source.
You can get those newer drivers from intel from here:
[https://01.org/linuxgraphics](https://01.org/linuxgraphics)

---

### Post by meltingpot2015 on 2016-03-22
So basically, Intel Graphics cards are Open Source. while AMD/ATI and Nvidia have Open Source and closed source (propriety) drivers?

[https://askubuntu.com/questions/178636/how-to-review-the-current-state-of-open-source-vs-closed-source-graphics-driver](https://askubuntu.com/questions/178636/how-to-review-the-current-state-of-open-source-vs-closed-source-graphics-driver)
[https://askubuntu.com/questions/334459/what-alternatives-are-there-to-nvidia-and-ati-graphics-cards](https://askubuntu.com/questions/334459/what-alternatives-are-there-to-nvidia-and-ati-graphics-cards)
[https://askubuntu.com/questions/90671/at-present-which-is-the-best-choice-for-a-ubuntu-graphics-card-amd-or-nvidia?rq=1](https://askubuntu.com/questions/90671/at-present-which-is-the-best-choice-for-a-ubuntu-graphics-card-amd-or-nvidia?rq=1)

I have the following driver:

00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400 / R3 Series]

and have just taken the leap to Ubuntu 15.10 and the open source graphics driver runs like a dream. 

For cards that have both propriety and open-source drivers the rule of thumb (general consensus) seems to be, use the propriety driver, only change to/keep open source driver if you encounter issues with the propriety driver or only need basic desktop task performance (i.e. I assume this means, if you don't use it for gaming, load heavy graphics applications etc.)

BTW: what was the solution to this thread?

---

