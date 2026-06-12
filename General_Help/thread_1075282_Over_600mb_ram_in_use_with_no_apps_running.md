---
title: "Over 600mb ram in use with no apps running?"
date: 2009-02-20
forum: General Help
---

### Post by FeraTech on 2009-02-20
Well I know first of all I'm using Intrepid after an upgrade. I know it's best to install from scratch but with the amount of information I have I opted against a fresh install.

Is there any way to track down what is eating up my ram? I checked the system monitor and even if I eliminate trackered and thunderbird something still takes up over 600mb.

I checked "top" and nothing was showing up with any significant ram usage. With windows XP I can get it down to 200-300 mb usage. Why is Ubuntu so high?

Also, I have desktop effects turned off.

---

### Post by albandy on 2009-02-20
The way linux uses RAM is completely different from windows. In use don't means that could no be used. Means that in this moment is being used for caching improving system speed, but when an application needs it could be used without problems.

do

cat /proc/meminfo

and you will see the memory usage.

---

### Post by FeraTech on 2009-02-20
MemTotal:      2056144 kB
MemFree:        120576 kB
Buffers:         22396 kB
Cached:         815460 kB
SwapCached:       1904 kB
Active:        1189776 kB
Inactive:       521376 kB
SwapTotal:     6040400 kB
SwapFree:      6029860 kB
Dirty:            2100 kB
Writeback:           0 kB
AnonPages:      872000 kB
Mapped:         110036 kB
Slab:           152944 kB
SReclaimable:   115488 kB
SUnreclaim:      37456 kB
PageTables:      22376 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:   7068472 kB
Committed_AS:  1745172 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    307736 kB
VmallocChunk: 34359430139 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:   1774464 kB
DirectMap2M:    321536 kB

Not sure which one is direct usage?

---

### Post by sdennie on 2009-02-20
Check:

```

free -m

```

The second row of information shows "actual" memory usage.  The cache and buffers can be considered free memory that is being used to speed your system up but can be dropped if your applications actually need that memory.

---

### Post by FeraTech on 2009-02-20
total       used       free     shared    buffers     cached
Mem:          2007       1921         86          0        252        616
-/+ buffers/cache:       1052        955
Swap:         5898          5       5893

That is with 2 firefox windows open...

---

### Post by binbash on 2009-02-20
This is normal.Windows and linux ram management is totally different.

---

### Post by FeraTech on 2009-02-20
I see...

Anybody care to elaborate how it works? I'm kind of curious...

---

### Post by albandy on 2009-02-21
[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by FeraTech on 2009-02-21
Wow thanks that was very interesting.

I didn't know that linux shared libraries were only loaded once into memory. That makes sense.

---

