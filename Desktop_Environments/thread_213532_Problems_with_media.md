---
title: "Problems with media"
date: 2006-07-11
forum: Desktop Environments
---

### Post by JackofArcades on 2006-07-11
Anything I try to view - flash movies, local movies, or music, simply doesn't work well. During playback it'll pause for an extended period of time. For example, while listening to a song, it may stop off and on for minutes at a time. It's not the media players (I've tried all of em) and it's not the engine I'm using (this happens on Xine, Gstreamer, and Arts). What's going on?

---

### Post by Thund3rstruck on 2006-07-11
what does your cpu utilization look like?

```

$ top

$ cat /proc/cpuinfo

```

---

### Post by JackofArcades on 2006-07-11
Here's the output for both:

```
top - 11:40:49 up 2 days, 17:39,  2 users,  load average: 0.41, 0.51, 0.68
Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.2% us,  0.7% sy,  0.0% ni, 80.8% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:   1017664k total,   974576k used,    43088k free,    54396k buffers
Swap:  2980016k total,    27732k used,  2952284k free,   608436k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
10274 darrel    15   0  145m  73m  18m S 13.3  7.4   9:11.05 firefox-bin
11895 darrel    15   0 43144  13m 9308 S  3.7  1.4   0:01.37 gnome-terminal
 3693 root      15   0  220m  84m 8792 S  1.7  8.6  43:28.99 Xorg
    1 root      16   0  1568  484  456 S  0.0  0.0   0:01.09 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:20.13 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:01.18 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.79 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
  136 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  135 root      15   0     0    0    0 S  0.0  0.0   0:11.69 kswapd0
  724 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
 1829 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata/0
 1830 root      13  -5     0    0    0 S  0.0  0.0   0:00.00 ata_hotplug/0


```


```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Celeron(R) CPU 2.80GHz
stepping        : 1
cpu MHz         : 2793.756
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pni monitor ds_cpl cid xtpr
bogomips        : 5592.18

```

---

