---
title: "Not all RAM detected"
date: 2008-12-17
forum: General Help
---

### Post by jkazda on 2008-12-17
Hi all,

I'm very new to Ubuntu, so be patient with me, please.

I have a Toshiba P100 notebook with 4GB of RAM (2x2GB). Therefore I decided to install 64bit version of Ubuntu Desktop. However, when I look in /proc/meminfo, i can see just 3GB of memory is detected. Can anyone help me in investigating what's wrong?

My current system information:
```
$ uname -a
Linux juraj-nb 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

```

and

```
$ more /proc/meminfo
MemTotal:      3088016 kB
MemFree:       2492840 kB
Buffers:         13532 kB
Cached:         211952 kB
SwapCached:          0 kB
Active:         358808 kB
Inactive:       125492 kB
SwapTotal:      915664 kB
SwapFree:       915664 kB
Dirty:               0 kB
Writeback:           0 kB
AnonPages:      258816 kB
Mapped:          58764 kB
Slab:            43340 kB
SReclaimable:    20604 kB
SUnreclaim:      22736 kB
PageTables:      15440 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   2459672 kB
Committed_AS:   591320 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    313368 kB
VmallocChunk: 34359424507 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:     33344 kB
DirectMap2M:   3110912 kB

```

This is my notebook configuration (taken from HWINFO32 under Windows - I just don't know how to get such information under Ubuntu yet :-) so I have dual boot currently):
```

Computer:      TOSHIBA Satellite P100
CPU:           Intel Core 2 Duo T7400 (Merom, B2)
               2166 MHz (13.00x166.7) @ 2173 MHz (13.00x167.2)
Motherboard:   TOSHIBA Satellite P100
Chipset:       Intel 945PM (Calistoga-PM) + ICH7-M/U
Memory:        4096 MBytes @ 334 MHz, 5.0-5-5-15
               - 2048 MB PC6400 DDR2-SDRAM - Samsung M4 70T5663QZ3-CF7 
               - 2048 MB PC6400 DDR2-SDRAM - Samsung M4 70T5663QZ3-CF7 
Graphics:      nVIDIA GeForce Go 7900 GS [Toshiba]
               nVIDIA GeForce Go 7900 GS (G71M), 512 MB GDDR3 SDRAM
Drive:         FUJITSU MHV2200BT PL, 195.4 GB, Serial ATA 1.5Gb/s
Drive:         MATSHITA DVD-RAM UJ-841S, DVD+R DL
Drive:         DI0085W WSJ431I, DVD-ROM
Sound:         Intel 82801GB ICH7 - High Definition Audio [B0]
Network:       Intel(R) PRO/1000 PL Network Connection
Network:       Intel(R) PRO/Wireless 3945ABG Network Connection
Network:       1394 Net Adapter
Network:       Microsoft Loopback Adapter
OS:            Microsoft Windows XP Professional Build 2600

```

I will be very happy, if someone can help me in understanding and solving this problem.

Thanks in advance.

Regards,
Juraj

---

### Post by Sam Lars on 2008-12-17
I would look in the BIOS to see if it indicates 4 GB.  If it does, look for any options about high memory to see if it's set to use all 4 GB.

---

### Post by jespdj on 2008-12-17
This is a frequently asked question.

Many computers have an option called "memory remapping" or something similar in the BIOS settings. You have to set this to **enabled**, otherwise the video card and other devices in your computer will allocate part of the address space, which makes part of your RAM inaccessible.

What video card do you have? Do you have a video card that has its own dedicated video memory, or does your video card use part of the main memory? If it's the latter, then the OS will obviously also not be able to use the full 4 GB.

*edit*: Ah, I see that you have a: nVIDIA GeForce Go 7900 GS (G71M), 512 MB GDDR3 SDRAM - so you do have a video card with its own memory.

---

### Post by jkazda on 2008-12-17
Hi Sam,

thank you for quick response! I forget to write it in my original post... I've searched in forums first and find a note about it can be in BIOS, but looks like it's not - it reports 4GB. I've tried to find any memory related setting in it, but it's Phoenix BIOS and it has not so much fields to set up. Unfortunately, I'm not a hardware guy and I just don't understand few fields in it, however, by logic there is nothing to set. But to be sure, I will check it again, maybe I will find some "Advanced settings" section I haven't noticed before.

Regards,
Juraj

---

### Post by neur0 on 2008-12-17
Just to be sure, can you paste the output of:

```
sudo dmidecode | grep Size
```

---

### Post by jkazda on 2008-12-17
> **neur0 said:**
> Just to be sure, can you paste the output of:

```
sudo dmidecode | grep Size
```

Hi neur0,

here it is:

```

$ sudo dmidecode | grep Size
	Runtime Size: 94464 bytes
	ROM Size: 64 kB
	Installed Size: 16 KB
	Maximum Size: 16 KB
	Installed Size: 4096 KB
	Maximum Size: 512 KB
	Size: 2048 MB
	Size: 2048 MB
	Range Size: 4 GB
	Range Size: 2 GB
	Range Size: 2 GB

```

Interesting command, thanks!

In the meanwhile, I was googling around for the only field I can't understand in my BIOS and it was "Execute-disable bit". May the value of this field has impact to memory size available for system?

Thank you.

Regards,
Juraj

---

### Post by Sam Lars on 2008-12-17
No, that is a security feature that shouldn't affect how much memory the system sees.

---

### Post by jkazda on 2008-12-19
So far, I've tried everything I was able google for, including blacklisting intel_agp (which I anyway didn't expect to work) and upgrading BIOS. Nothing helped.

The only thing I'm not sure about is that some internet resources say I have to compile custom kernel with high memory support and some say that 64bit branch of Ubuntu has this by default. I would say that it is logical that it is there by default, but can someone confirm this to me?

Thank you.

Regards,
Juraj

---

### Post by jkazda on 2008-12-19
Sam, now when I'm reading your answer one more time, I'm not sure if I understand it right: you mean checking high memory options in BIOS or in Ubuntu? If in Ubuntu, can you tell me what and how I can check these things?

Thank you in advance.

Regards,
Juraj

---

### Post by Sam Lars on 2008-12-19
The 32-bit kernel wouldn't have support for high memory, but the 64-bit should by default.
You could try compiling your own kernel, but I don't think the problem is that that option is not enabled.
The BIOS is where you should check... but you said you didn't find anything, so I don't know.
Did you buy the notebook with 4 GB of RAM?  Have you ever been able to use it all?

---

