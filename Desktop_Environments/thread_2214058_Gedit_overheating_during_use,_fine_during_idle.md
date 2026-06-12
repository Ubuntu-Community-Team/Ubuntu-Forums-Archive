---
title: "Gedit overheating during use, fine during idle"
date: 2014-03-30
forum: Desktop Environments
---

### Post by Lars Noodén on 2014-03-30
Editing in Gedit causes the CPU to overheat and the fan to kick into high gear when I am actively editing:

```

Mar 30 13:50:48 lubuntu dbus[482]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Mar 30 13:50:48 lubuntu dbus[482]: [system] Successfully activated service 'org.freedesktop.hostname1'
Mar 30 13:51:36 lubuntu kernel: [212933.326558] CPU2: Core temperature above threshold, cpu clock throttled (total events = 7467)
Mar 30 13:51:36 lubuntu kernel: [212933.326559] CPU6: Core temperature above threshold, cpu clock throttled (total events = 7467)
Mar 30 13:51:36 lubuntu kernel: [212933.326562] CPU4: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.326564] CPU5: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.326566] CPU1: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.326567] CPU0: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.326569] CPU3: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.326571] CPU7: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.326572] CPU6: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.326585] CPU2: Package temperature above threshold, cpu clock throttled (total events = 14104)
Mar 30 13:51:36 lubuntu kernel: [212933.327540] CPU2: Core temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327541] CPU6: Core temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327543] CPU4: Package temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327544] CPU0: Package temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327546] CPU1: Package temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327547] CPU3: Package temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327550] CPU7: Package temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327551] CPU5: Package temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327552] CPU6: Package temperature/speed normal
Mar 30 13:51:36 lubuntu kernel: [212933.327561] CPU2: Package temperature/speed normal

```

When it is open but just idle, there is nothing special about the temperature.  

top shows nothing suspicious:

```

top - 13:51:57 up 4 days, 15:26,  8 users,  load average: 2,48, 0,89, 0,51
Tasks: 257 total,   1 running, 241 sleeping,   0 stopped,  15 zombie
%Cpu(s):  0,5 us,  0,3 sy,  0,0 ni, 99,2 id,  0,0 wa,  0,0 hi,  0,0 si,  0,0 st
KiB Mem:   3956768 total,  3388944 used,   567824 free,   151620 buffers
KiB Swap:  3905532 total,   165824 used,  3739708 free.  1463960 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
16235 user      20   0  893180 170964  41740 S   2,3  4,3   2:14.47 firefox     
 4744 user      20   0 1284668 246784  35460 S   1,3  6,2  13:55.04 thunderbird 
16047 user      20   0   31556   1780   1192 S   0,7  0,0   1:19.75 top         
  108 root      20   0       0      0      0 S   0,3  0,0   0:27.13 kworker/6:1 
 2525 root      20   0  359552 118316  21408 S   0,3  3,0 190:06.17 Xorg        
 3699 user      20   0  563388  15572   8344 S   0,3  0,4   2:41.42 x-terminal+ 
21520 user      20   0   31424   1768   1180 R   0,3  0,0   0:00.03 top         
22196 user      20   0 1560076  26232  10996 S   0,3  0,7   6:26.54 transmis

```

It happens pretty much every time I resume editing.  

What should I look for to identify the cause of the problem?

---

### Post by Lars Noodén on 2014-03-30
It's the ibus-daemon flaring up, *very* briefly.  

```

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 2730 user      20   0  373672  23440   1740 R 172,6  0,6  45:11.21 ibus-daemon 
 2756 user      20   0  285672   3660   2604 S 105,9  0,1  26:31.45 ibus-x11    
 2525 root      20   0  358760 118124  21216 S  87,6  3,0 197:29.28 Xorg        
11441 user      20   0  971708  73700  17856 S  81,3  1,9  13:22.85 gedit       

```

Very hard to catch it in top.

---

### Post by trag on 2014-04-16
Improving power management may help,install TLP from repositories.
sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw
If you haven't thought of it all ready,clean the fan and vents with canned air.Picking up a Laptop cooling pad would be something to consider.
good luck
trag

---

