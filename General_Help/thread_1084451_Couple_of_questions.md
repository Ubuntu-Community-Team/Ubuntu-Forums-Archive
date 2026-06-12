---
title: "Couple of questions"
date: 2009-03-02
forum: General Help
---

### Post by r0yalty on 2009-03-02
Hello, 

I 'm new to Linux and just installed Ubuntu 8.10 x64. I have 8 Gb of ram and typing free -m shows the following:
           total       used       free     shared    buffers     cached
Mem:          7991       7937         54          0         57       6422

This is when I have hardly any stuff running. Isnt the OS using a bit to much?

top shows:
p - 08:50:46 up 17:33,  4 users,  load average: 1.25, 3.03, 4.22
Tasks: 181 total,   1 running, 179 sleeping,   0 stopped,   1 zombie
Cpu(s): 13.0%us,  2.3%sy,  0.0%ni, 65.0%id, 17.6%wa,  0.3%hi,  1.8%si,  0.0%st
Mem:   8183668k total,  8137672k used,    45996k free,   161916k buffers
Swap:  3906240k total,     5908k used,  3900332k free,  6499564k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND           
 7353 r0yalty   20   0  961m 313m  33m S   19  3.9  21:08.02 java              
 6072 root      20   0  526m 112m  16m S    7  1.4  41:55.90 Xorg              
16332 r0yalty   20   0 95452  31m  10m S    7  0.4   1:49.93 npviewer.bin      
 6488 r0yalty   20   0  367m  75m  33m S    2  0.9  17:56.80 compiz.real       
11384 root      15  -5     0    0    0 S    1  0.0   1:57.77 kjournald       

However, when i run the System Monitor and click the Resources tab, the Memory graph shows only 1.4 GiB ( 18.2 % ) of 7.8 GiB as use .. Which should I trust??


Also, another question. Whenever i unpack archives or copy files, my Vuze (aka Azureus) stops all downloads and my FireFox goes gray.

---

### Post by WatchingThePain on 2009-03-02
Hi,

free -m displays in MB without m is in KB.
How about cat /proc/meminfo

---

### Post by heindsight on 2009-03-02
You'll notice the second line of **free**'s output says someting about +/- buffers/cache and then lists somewhat less used memory and more free memory.

The Linux kernel uses otherwise unused memory for internal buffers and cache, as soon as any application needs memory however, it will release release some of that buffer/cache memory to the application.

---

