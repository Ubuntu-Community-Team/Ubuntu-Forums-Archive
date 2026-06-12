---
title: "ubuntu 8.10 got slow"
date: 2009-04-03
forum: General Help
---

### Post by entilete on 2009-04-03
hi
My problem is that a few days ago, my computer started working slower and I'm about to get mad because I don't know what to do. :sad:
It's more noticeable when I write on aMSN, the letter takes a bit to appear and Firefox uses a LOT the CPU.
the RAM is being used normally (400MB most of the time).
what could be the problem here? :confused:

btw, my PC configuration is:
Athlon X2 5600+
2 x 2 GB DDR II 800 mhz
1XPATA 120GB
1xSATA 250GB
GeForce 7300GT

---

### Post by xenophed on 2009-04-03
in term type top and see what is dragging it down and write back else network thing like autobot tiring to hack in had that happen before check with the netwatch program

---

### Post by asuastrophysics on 2009-04-03
entilete, what else do you have running in the background besides firefox?

open up system-monitor and sort by memory.

also, it might help to know how many tabs you have open in firefox. i know when i have a lot of tabs, firefox starts eating through a lot more ram. 

let me know

---

### Post by entilete on 2009-04-03
it seems that Wish and Xorg uses more the CPU, but if, for example, I want to see 2 videos at the same time in Firefox, the CPU is used over 50% and if I'm listening to music and I do something else in Firefox, the audio stops ¬¬. It's not normal, I'm used to do things like these and I'd never had this problem before.
asuastrophysics: the ram is not a problem, it rarely exceeds the 500MB
erm, something I forgot is that it takes longer to boot
here's what top says u.u:

[B]top - 14:49:24 up  1:29,  2 users,  load average: 1.04, 1.21, 1.28
Tasks: 123 total,   2 running, 121 sleeping,   0 stopped,   0 zombie
Cpu(s): 29.3%us,  4.9%sy,  0.0%ni, 65.6%id,  0.0%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   3371900k total,   913492k used,  2458408k free,    87364k buffers
Swap:  1108444k total,        0k used,  1108444k free,   367436k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6075 marcelo   20   0 97160  77m 6900 R   31  2.4  10:22.31 wish8.5            
 5431 root      20   0  140m  60m  12m S   13  1.8  11:35.05 Xorg               
 7352 marcelo   20   0  205m  60m  22m S   11  1.8   0:51.95 firefox            
 7206 marcelo   20   0  225m  48m  22m S    9  1.5   0:47.30 rhythmbox          
 5848 marcelo   20   0 32180 4680 3544 S    5  0.1   2:10.55 pulseaudio         
 5981 marcelo   20   0 82620  39m  11m S    3  1.2   3:23.93 compiz.real        
 5978 marcelo   20   0 21712 3336 1952 S    1  0.1   0:10.66 gnome-screensav    
 7464 marcelo   20   0  2416 1144  876 R    1  0.0   0:00.06 top                
    1 root      20   0  3056 1896  576 S    0  0.1   0:01.10 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.22 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.36 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.06 events/0[/B]

---

