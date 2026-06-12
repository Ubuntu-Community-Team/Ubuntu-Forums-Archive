---
title: "Available RAM detected incorrectly in 9.04"
date: 2009-04-28
forum: General Help
---

### Post by jefferybond on 2009-04-28
Just installed 9.04 desktop edition (32-bit) on a system with 4GB of ram installed (Sun Ultra 40M2).

The problem is that only about 2.5GB of ram is detected. I *know* that all 4GB wont be available on a 32-bit OS, but on Ubuntu 8.10 I was getting about 3.6GB available, which is about what I expected.

Why has this dropped to only 2.5GB in 9.04?

'uname -a' gives:

Linux bubble 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Some lines from 'dmesg':

[    0.000000] 1611MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
....
[    0.004000] Memory: 2505096k/2554880k available (4126k kernel code, 48440k reserved, 2208k data, 
532k init, 1649672k highmem)

Contents of /proc/meminfo:

MemTotal:        2513876 kB
MemFree:         1214256 kB
Buffers:           57092 kB
Cached:           871536 kB
SwapCached:            0 kB
Active:           570756 kB
Inactive:         638952 kB
Active(anon):     287936 kB
Inactive(anon):        0 kB
Active(file):     282820 kB
Inactive(file):   638952 kB
Unevictable:          16 kB
Mlocked:              16 kB
HighTotal:       1649672 kB
HighFree:         480252 kB
LowTotal:         864204 kB
LowFree:          734004 kB
SwapTotal:       2634620 kB
SwapFree:        2634620 kB
Dirty:                20 kB
Writeback:             0 kB
AnonPages:        281216 kB
Mapped:            90936 kB
Slab:              54228 kB
SReclaimable:      44064 kB
SUnreclaim:        10164 kB
PageTables:         2792 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     3891556 kB
Committed_AS:     686656 kB
VmallocTotal:     122880 kB
VmallocUsed:       48648 kB
VmallocChunk:      53236 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       40952 kB
DirectMap4M:      864256 kB

Is this a bug in the latest kernel?

Jeff

---

