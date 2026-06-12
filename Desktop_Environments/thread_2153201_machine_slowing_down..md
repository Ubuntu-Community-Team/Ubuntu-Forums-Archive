---
title: "machine slowing down."
date: 2013-06-10
forum: Desktop Environments
---

### Post by Tyson87 on 2013-06-10
Hello All, 

Recently my machine has been taking its time when Im opening the terminal. 

I have a quad core machine with 4 GB of ram. 

No high processing. 

I have listed the out put of top and free -m.

Any suggestions would be appreciated!

Thanks!


=====================================
server:~$ topUnknown HZ value! (409) Assume 100.
Warning: /boot/System.map-2.6.35-23-generic-pae has an incorrect kernel version.
 10:23pm  up  6:40, 32 users,  load average: 5.59, 7.10, 4.01
246 processes: 241 sleeping, 2 running, 1 zombie, 1 stopped
CPU states:  0.2% user,  7.1% system,  0.0% nice, 92.6% idle
Mem:  4120400K av, 1183748K used, 2936652K free,       0K shrd,    1768K buff
Swap: 3445904K av,  427832K used, 3018072K free                  879684K cached


  PID USER     PRI  NI  SIZE  RSS SHARE STAT  LIB %CPU %MEM   TIME COMMAND
 8437             20   0  374M  93M    32 R       0 23.4  2.3   0:02 top
 7591             20   0  235M 5464  1292 S       0  0.5  0.1   0:48 dropbox
   34 root      20   0     0    0     0 SW      0  0.2  0.0   0:01 kblockd/3
 2565 root      20   0  5612  116    64 S       0  0.2  0.0   0:02 udisks-daemon
 6141 root      20   0 60752 2988  1056 S       0  0.2  0.0   0:11 Xorg
 7556             20   0 84460 1236   560 S       0  0.2  0.0   0:02 avant-window-na
 7753             20   0 39572 2868  1984 S       0  0.2  0.0   0:00 clock-applet
 8436             20   0  2508 1196   836 R       0  0.2  0.0   0:00 top
    1 root      20   0  3016  476   140 S       0  0.0  0.0   0:00 init

-server:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          4023       1323       2700          0          3       1121
-/+ buffers/cache:        198       3825
Swap:         3365        518       2846

---

### Post by dino99 on 2013-06-10
your system might thanks you if you do some cleaning: clean/autoclean/autoremove/gtkorphan/bleachbit

---

### Post by deadflowr on 2013-06-11
I thought this line from top was wierd

> [COLOR=#000000]Warning: /boot/System.map-2.6.35-23-generic-pae has an incorrect kernel version.[/COLOR]

So looking around found this

[http://www.linuxquestions.org/questions/linux-server-73/warning-boot-system-map-2-6-32-37-generic-has-an-incorrect-kernelversion-ubuntu10-04-a-4175410801/](http://www.linuxquestions.org/questions/linux-server-73/warning-boot-system-map-2-6-32-37-generic-has-an-incorrect-kernelversion-ubuntu10-04-a-4175410801/)

You, of course, can look around for the many other reported instances of this.

---

