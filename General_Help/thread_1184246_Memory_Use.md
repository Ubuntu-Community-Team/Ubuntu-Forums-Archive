---
title: "Memory Use"
date: 2009-06-10
forum: General Help
---

### Post by racerraul on 2009-06-10
I've been searching for a solution to see what is taking up all my memory but am coming up empty.

Mem use has suddenly jumped and sustained at 6g of 8g ram.

However, system monitor does not show what process is taking up all that ram.

Nother is Top.

Bot utilities show the total and use correctly, but are not showing the process that is actually taking up all that memory.  And what is currently showing barely adds up to 500mb-1g of ram.

Is there another tool I can use to see actual memory use per process?

---

### Post by colau on 2009-06-10
> **racerraul said:**
> I've been searching for a solution to see what is taking up all my memory but am coming up empty.

Mem use has suddenly jumped and sustained at 6g of 8g ram.

However, system monitor does not show what process is taking up all that ram.

Nother is Top.

Bot utilities show the total and use correctly, but are not showing the process that is actually taking up all that memory.  And what is currently showing barely adds up to 500mb-1g of ram.

Is there another tool I can use to see actual memory use per process?

```

sudo apt-get install htop

```

---

### Post by iponeverything on 2009-06-10
Do a "free" and you will see that extra memory is going for buffers/cache. This is good thing and it given back if the system needs it.

---

### Post by Gizenshya on 2009-06-10
would you mind explaining this in more detail? (including the commandline for doing that...)

and why doesn't mine do that?

(sorry for kindof off-topic)

---

### Post by racerraul on 2009-06-10
free
```
racerraul@raul-6000:~$ free
             total       used       free     shared    buffers     cached
Mem:       8183504    7726228     457276          0      78292     718440
-/+ buffers/cache:    6929496    1254008
Swap:      9861484       5332    9856152

```

Doesn't look like that is where the mem is being used...

htop is a very cool utility... but didn't help show what is taking all that memory.

---

### Post by colau on 2009-06-11
> **racerraul said:**
> free
```
racerraul@raul-6000:~$ free
             total       used       free     shared    buffers     cached
Mem:       8183504    7726228     457276          0      78292     718440
-/+ buffers/cache:    6929496    1254008
Swap:      9861484       5332    9856152

```

Doesn't look like that is where the mem is being used...

htop is a very cool utility... but didn't help show what is taking all that memory.
```

cat /proc/meminfo
free -m

```

---

### Post by racerraul on 2009-06-11
```
MemTotal:      8183504 kB
MemFree:        354696 kB
Buffers:         78692 kB
Cached:         726268 kB
SwapCached:       3016 kB
Active:         572696 kB
Inactive:       462240 kB
SwapTotal:     9861484 kB
SwapFree:      9856152 kB
Dirty:              24 kB
Writeback:           0 kB
AnonPages:      226944 kB
Mapped:          84512 kB
Slab:          6665124 kB
**SReclaimable:  6628372 kB**
SUnreclaim:      36752 kB
PageTables:       9124 kB
NFS_Unstable:        0 kB
Bounce:              0 kB
WritebackTmp:        0 kB
CommitLimit:  13953236 kB
Committed_AS:   443548 kB
VmallocTotal: 34359738367 kB
VmallocUsed:    334312 kB
VmallocChunk: 34359404019 kB
HugePages_Total:     0
HugePages_Free:      0
HugePages_Rsvd:      0
HugePages_Surp:      0
Hugepagesize:     2048 kB
DirectMap4k:   3789696 kB
DirectMap2M:   4597760 kB
racerraul@raul-6000:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7991       7646        345          0         76        709
-/+ buffers/cache:       6859       1132
Swap:         9630          5       9625

```

So that SReclaimable: memory is actually not in use?

---

### Post by racerraul on 2009-06-11
found this...
[http://www.faqs.org/docs/linux_admin/buffer-cache.html](http://www.faqs.org/docs/linux_admin/buffer-cache.html)

And I guess I understand things a bit better.  However... this is the first time that I notice it (since it showed up in conky).

Shouldn't this be showing up all the time?

This is what is making the memory query in conky.
```
${font Newtext Rg BT:size=10}${color Black}$alignc $mem / $memmax $alignr $memperc%
```

---

