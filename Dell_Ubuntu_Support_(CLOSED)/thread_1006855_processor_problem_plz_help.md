---
title: "processor problem? plz help"
date: 2008-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pibb69173 on 2008-12-09
ok so heres the low down on whats happened

i received a laptop a few months ago and had windows( yea i know gross) and since windows fails so hard i wiped my hard drive and did a fresh install of ubuntu 8.10 last night and im sitting here wondering why is my computer so laggy i  shrug it of as my video card for a while so a few hours ago i install the video card correctly, runs a bit better and all, but it was still laggy so i start messing around with the apps and i look at my system monitor and see that it is constantly running around 88% +.      and as having linux on my desktop i know this is completely wrong so i know am coming to the community for help :?


specs for my laptop

Dell Latitude D600
768Mb ram
1.4Ghz processor
32Mb mobility radeon 9000 video card
30Gig hard drive

any help is much apreciated any help relitivly soon is great cuz i dont want my comp to die, will keep searching the boards in the meen time

---

### Post by anjilslaire on 2008-12-09
```

top

```

This will show whats using the most ram & cpu

---

### Post by pibb69173 on 2008-12-09
```
top - 20:47:29 up  5:37,  2 users,  load average: 2.18, 2.36, 3.14
Tasks: 116 total,   7 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s): 24.8%us, 71.5%sy,  0.0%ni,  2.0%id,  0.0%wa,  1.3%hi,  0.3%si,  0.0%st
Mem:    773464k total,   762568k used,    10896k free,    28832k buffers
Swap:  1253028k total,    19396k used,  1233632k free,   378188k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   51 root      15  -5     0    0    0 R 36.8  0.0 118:54.33 kacpi_notify       
   50 root      15  -5     0    0    0 S 31.5  0.0 101:07.87 kacpid             
 1458 root      20   0 74320  21m 9396 R 10.3  2.9   2:53.36 Xorg               
 2556 agent     20   0  172m  80m  21m S  4.3 10.6   3:10.47 firefox            
 2523 agent     20   0 21520  12m 7816 S  2.0  1.7   0:09.64 metacity           
 1621 agent     20   0 38724  22m  12m S  1.3  2.9   0:13.60 gnome-panel        
26951 root      20   0 54700  40m  22m R  1.3  5.4   0:11.96 synaptic           
26974 root      20   0  5152 1980 1664 R  1.3  0.3   0:01.92 http               
 1571 root      15  -5     0    0    0 S  0.7  0.0   1:49.29 scsi_eh_1          
 1656 agent     20   0 29756  16m  10m S  0.7  2.2   0:02.92 cpufreq-applet     
 1690 agent     20   0 27440  15m 9.8m R  0.7  2.0   0:02.62 update-notifier    
27202 agent     20   0 91624  22m  12m R  0.7  3.0   0:01.06 gnome-terminal     
    1 root      20   0  3056  564  508 S  0.0  0.1   0:01.70 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.70 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/
```

thats a quick kopie of it :/  ..... and... it runs fine on startup then it starts too laggg? processer and all that

---

### Post by pibb69173 on 2008-12-09
OK not solved.... i found out that when i put it into suspend then bring it ot thats when the processor starts going crazy at 100% and so on but it runs normally when i dont put it into suspend :/

---

### Post by pibb69173 on 2008-12-10
ahhh..... plz help? if i figure anything else out will post more info...

---

