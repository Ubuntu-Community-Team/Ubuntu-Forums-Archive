---
title: "Xorg uses 600MB of RAM in Gutsy?"
date: 2007-11-10
forum: Desktop Environments
---

### Post by c-shadow on 2007-11-10
Is it normal for Xorg to use RAM like this (PID 24584):

```

top - 22:02:41 up 4 days, 2 min,  3 users,  load average: 0.66, 0.68, 1.06
Tasks: 188 total,   2 running, 185 sleeping,   0 stopped,   1 zombie
Cpu(s): 14.8%us,  4.1%sy,  0.0%ni, 80.6%id,  0.0%wa,  0.0%hi,  0.5%si,  0.0%st
Mem:   2075944k total,  1998024k used,    77920k free,   154392k buffers
Swap:  2096472k total,   491356k used,  1605116k free,   579100k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                        
 8900 alen      16   0 33112  20m  14m S   19  1.0   0:40.22 gnome-system-mo                                                                
 9017 elly      15   0  284m 174m  22m R   11  8.6   1:43.41 firefox-bin                                                                    
14869 root      15   0  137m  91m   9m S    6  4.5 329:45.47 Xorg                                                                           
 8875 alen      15   0  253m 121m  25m S    2  6.0   0:56.80 firefox-bin                                                                    
 9113 alen      15   0  2500 1212  876 R    0  0.1   0:00.03 top                                                                            
24584 root      15   0  624m 604m 9284 S    0 29.8   6:24.34 Xorg                                                                           
    1 root      18   0  2952  536  484 S    0  0.0   0:01.36 init   

```

Or is it some memory leak?
I don't remember seeing it behave like this in feisty...these is also >400 MB of swap in use...

---

