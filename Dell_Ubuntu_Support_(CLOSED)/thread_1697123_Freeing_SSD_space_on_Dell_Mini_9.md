---
title: "Freeing SSD space on Dell Mini 9"
date: 2011-02-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shuey_p on 2011-02-28
My Dell Mini 9 has a very small SSD, but a 16 GB flash drive. My primary drive (SSD) is nearly full, and I would like to delete unnecessay file, or transfer them to the 16 GB flash drive.

I cannot see to find the process for accomplishing this task.

Any help will be appreciated.

Thank you,
Phil Shuey

---

### Post by KegHead on 2011-02-28
Hi!

I'd like to know also.

I have a 16gb ssd.

KegHead

---

### Post by emptythevoid on 2011-03-01
A question for both of you - are you running Dell's special Ubuntu 8.04, or if not, does your install of Ubuntu include a swap partition?

---

### Post by KegHead on 2011-03-01
Hi!

Ubuntu 10.10 desktop.

No Swap.

KegHead

---

### Post by KegHead on 2011-03-01
My info:


jim@jim-desktop:~$ cat /proc/meminfo
MemTotal:        2050972 kB
MemFree:         1343856 kB
Buffers:           53408 kB
Cached:           364512 kB
SwapCached:            0 kB
Active:           332776 kB
Inactive:         305636 kB
Active(anon):     220944 kB
Inactive(anon):    81920 kB
Active(file):     111832 kB
Inactive(file):   223716 kB
Unevictable:         144 kB
Mlocked:             144 kB
HighTotal:       1177960 kB
HighFree:         580652 kB
LowTotal:         873012 kB
LowFree:          763204 kB
SwapTotal:       6008272 kB
SwapFree:        6008272 kB
Dirty:                68 kB
Writeback:             0 kB
AnonPages:        220640 kB
Mapped:            70016 kB
Shmem:             82376 kB
Slab:              24720 kB
SReclaimable:      14436 kB
SUnreclaim:        10284 kB
KernelStack:        2384 kB
PageTables:         4868 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     7033756 kB
Committed_AS:     977416 kB
VmallocTotal:     122880 kB
VmallocUsed:       27576 kB
VmallocChunk:      88816 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       20472 kB
DirectMap4M:      888832 kB
jim@jim-desktop:~$

---

### Post by emptythevoid on 2011-03-02
Steps 3 and 4 are good, and using the Disk Usage Analyzer can be helpful in figuring out what particular things might be taking up space:
[http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07](http://maketecheasier.com/8-ways-to-maintain-a-clean-lean-ubuntu-machine/2008/10/07)

You can also remove old linux kernels that your system isn't using anymore.  I'd leave at least one or two, just in case the current kernel breaks or has issues.
[http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

I've been using a Dell Mini 9 with an 8GB SSD and I'm able to get by.

---

### Post by KegHead on 2011-03-02
Hi!

OOPS!

I pasted my desktop info!

My Dell mini 9 runs great w/2gb ram.

KegHead

---

### Post by shuey_p on 2011-03-02
In response to empty the void. Yes, I have Ubuntu 8.04. I have no idea about swap partition feature -- as to whether I have it or not. (Or even how to check).

Thanks,
Phil Shuey

---

### Post by KegHead on 2011-03-02
Hi shuey_p!

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

You'll find tons of info.

KegHead

---

### Post by ugm6hr on 2011-03-03
```
sudo apt-get clean
```
Delets all the installed updates & apps from /var/cache/apt/archives
Backup first if you want to

---

### Post by KegHead on 2011-03-03
Hi!

I forgot about:

sudo apt-get clean

I should use this more often.

KegHead

---

