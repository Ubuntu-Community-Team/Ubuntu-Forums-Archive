---
title: "Printer software hogging resources"
date: 2009-06-23
forum: General Help
---

### Post by Weidbrewer on 2009-06-23
The other day, my printer quit working.  No big deal, I rarely use it.  However, I started noticing that one core of my CPU was being completely used by something.  Checking the GUI processes list, nothing unusual was there.  However, here's what I got in terminal:

```
weidbrewer@*****:~$ top

top - 23:00:05 up 1 day,  3:52,  2 users,  load average: 1.02, 1.05, 1.01
Tasks: 178 total,   4 running, 174 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.0%us, 41.3%sy,  0.0%ni, 49.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2851780k total,  2057848k used,   793932k free,   204188k buffers
Swap:        0k total,        0k used,        0k free,  1215736k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5793 lp        20   0  9100 6924 1044 R  100  0.2 869:26.40 cifip1800          
 6806 root      20   0 55936 1760 1168 S    1  0.1   5:26.71 collectd           
27675 weidbrew  20   0  112m  24m  13m R    1  0.9   0:00.78 gnome-terminal     
27717 weidbrew  20   0  2548 1180  876 R    1  0.0   0:00.34 top                
 6684 root      20   0  345m  37m  11m R    0  1.4  20:59.73 Xorg             
```


Notice that cifip1800 is hogging it up.  No idea why.  No jobs are pending, and it is unaffected by unplugging the printer.   If I reboot, everything is groovy for a while, but then I'll come back later in the day and the system is bogged down.

Anyone know a way to either A.) fix this or B.) kill it?

---

