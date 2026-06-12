---
title: "Ubuntu keep freezeee!"
date: 2012-08-10
forum: Desktop Environments
---

### Post by CurseThePhobia on 2012-08-10
Hey Guys.
I am new with ubuntu and i just install Ubuntu 12.04 LTS 32-Bit along my beloved Windows. Im not dare to remove my windows because it is the bost of the PC on my laptops. So, this is the problem. I see ubuntu is an awesome Operating System, but when i try it, i have done all the 'what to do after installing ubuntu' including like updates, flash and so on. But when i want to have a tried on it, its keep FREEZE. and freeze and free and freezeeeee. That was so very annoying for every computer user...I have used windows but there are no such freeze happen at all. But when i using ubuntu, i freeze at all...well, this is my PC reference:
---------------------------------------------------
Computer: Acer Aspire 4250
Processor: AMD Dual-Core Processor E450
Graphic Card: AMD Radeon HD 6320 (The 4th class GC)
RAM: 2GB
---------------------------------------------------
Well, i heard that Ubuntu runs smooth on 1GB of ram. Just heard, but in my case, i freezingin 2GB of ram. Well, that was awkward. So, any improvement or fixing about this problem. Please guys, i just wanna put ubuntu part of ma Life...thats all...:(:(:(:(:(

---

### Post by johnathansmith on 2012-08-10
Could you go in terminal type:
```
top
```
then post here your results please.

---

### Post by CurseThePhobia on 2012-08-11
cursethephobia@ubuntu:~$ top

top - 18:49:48 up 7 min,  2 users,  load average: 0.31, 0.69, 0.43
Tasks: 171 total,   1 running, 170 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.5%us,  6.1%sy,  0.0%ni, 78.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1781352k total,  1654040k used,   127312k free,   502668k buffers
Swap:   262140k total,       48k used,   262092k free,   578840k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1692 cursethe  20   0  274m  98m  38m S   17  5.6   0:48.01 compiz             
 1052 root      20   0  244m  95m  55m S   12  5.5   0:25.13 Xorg               
 2467 cursethe  20   0 89376  14m  10m S    8  0.8   0:01.46 gnome-terminal     
 2531 cursethe  20   0  2836 1168  880 R    1  0.1   0:00.19 top                
    9 root      20   0     0    0    0 S    0  0.0   0:00.49 kworker/1:0        
 2332 cursethe  20   0  209m  67m  21m S    0  3.9   0:12.72 chrome             
    1 root      20   0  3520 1988 1312 S    0  0.1   0:01.43 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.46 kworker/0:0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/1        
   11 root      20   0     0    0    0 S    0  0.0   0:00.07 kworker/0:1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset

---

### Post by johnathansmith on 2012-08-12
Could you suspend your desktop effects, and watch if computer still freezing? If it's not, i assume there is problem with your graphic card drivers.

---

### Post by CurseThePhobia on 2012-08-16
How to done that?..

---

### Post by Bigtime_Scrub on 2012-08-16
> **CurseThePhobia said:**
> How to done that?..

Log out and when you log back in choose Ubuntu 2-D from your choice of sessions. If it stops freezing it could be a graphics driver.If the freezes continue it is something else, maybe bad RAM or there was a problem with the install media...

---

### Post by CurseThePhobia on 2012-08-17
Well.. My problem solve for itself. Im also weird on what had happening. I just keep using it. If i not mistake, i open ubuntu 6 time, uninstall my graphic card driver about 4 times and install it back about 4 times also. When i restart my ubuntu back, it had no freeze. (actually, it has to, but not very worse than before). BTW, thanks for helping me guys!

---

