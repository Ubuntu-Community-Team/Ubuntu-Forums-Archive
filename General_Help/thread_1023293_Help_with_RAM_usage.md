---
title: "Help with RAM usage"
date: 2008-12-27
forum: General Help
---

### Post by justjoshingyou on 2008-12-27
I have a problem with RAM usage. I have have 1024mb of DDR2 Dual Channel RAM and my graphics card is an Intel Graphics Media Accelerator X3000 with up to 224 MB DDR Shared Video Memory (with 1 PCI Express slot available). When I turn my PC on the ram usage app on the panel says something around 50% used by programs and 30% used by cache if I leave it alone for a couple hours the pc becomes so slow that I have to restart. I dual boot with Windows XP Media Center Edition and it does not use as much RAM as Ubuntu does. Some more specs are:

OS: Ubuntu Intrepid Ibex (8.10)
Model: Gateway GT5238E
Processor: Intel Core2Duo E6300 each core @ 1.86 GHz, 2 MB L2 cache, 1066 MHz FSB  (with VIIV)
Swapiness: Default (60?)
top:

```
josh@josh-office:~$ top

top - 19:32:37 up 40 min,  2 users,  load average: 0.07, 0.05, 0.07
Tasks: 138 total,   1 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.1%us,  0.5%sy,  0.0%ni, 97.2%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   1007304k total,   686076k used,   321228k free,    16412k buffers
Swap:  6514316k total,        0k used,  6514316k free,   195904k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5371 root      20   0  464m  97m 8284 S    4  9.9   1:07.05 Xorg               
 6107 josh      20   0 92388  22m  12m S    3  2.3   0:01.48 gnome-terminal     
 5825 josh      20   0 23536  15m 6120 S    1  1.6   0:10.54 compiz.real        
 5984 josh      20   0  181m  72m  22m S    1  7.3   1:02.75 firefox            
    1 root      20   0  3056 1884  564 S    0  0.2   0:01.34 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.18 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   51 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   52 root      15  -5     0    0    0 S    0  0.0   0:00.00 kintegrityd/1    
```

---

### Post by binbash on 2008-12-27
what is the output of free -m

---

### Post by justjoshingyou on 2008-12-27
```
josh@josh-office:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           983        950         33          0        243        203
-/+ buffers/cache:        503        480
Swap:         6361          0       6361
```


sorry about that...

---

### Post by hyper_ch on 2008-12-28
unused ram = waste ram

What do you need to have 1gb ram for if you don't use it? Linux handles ram a lot more different than windows.

The important part is this:
```

load average: 0.07, 0.05, 0.07

```

---

### Post by Greyed on 2008-12-28
> **justjoshingyou said:**
> if I leave it alone for a couple hours the pc becomes so slow that I have to restart.

You did good showing us the output of top.  Problem is it looks like that it was from just after your machine had booted and not after leaving it alone for hours and when it is slow.

---

