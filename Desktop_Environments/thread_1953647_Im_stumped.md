---
title: "Im stumped"
date: 2012-04-06
forum: Desktop Environments
---

### Post by Insomn1a on 2012-04-06
ok, so I've reinstall Ubuntu 10.10 on this desktop here, and im running into the following symptoms:


-No Desktop Icons
-Cannot open any programs 
-Cannot open system monitor
-high cpu utilization but no process has over 10% usage, mostly XORG is taking it up when running the desktop environment.
-the window selector at the bottom of the screen creates what looks like infinite instances of the file browser trying to open a directory, but it cant, Ive uninstalled all of the programs that i put onto the fresh install and its still doing all of the above.


I tried to start the system monitor through terminal and get the following output:

ghamlin@ghamlin-desktop:~$ gnome-system-monitor
gnome-system-monitor: symbol lookup error: /usr/lib/libgiomm-2.4.so.1: undefined symbol: g_application_get_type
ghamlin@ghamlin-desktop:~$ ^C
ghamlin@ghamlin-desktop:~$ 



Here is my TOP output:

```

ghamlin@ghamlin-desktop:~$ top

top - 17:03:44 up 21 min,  4 users,  load average: 3.82, 3.80, 3.04
Tasks: 159 total,   3 running, 155 sleeping,   0 stopped,   1 zombie
Cpu(s): 39.1%us, 18.6%sy,  0.0%ni, 41.8%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   5533404k total,  1334328k used,  4199076k free,    49828k buffers
Swap:  9936892k total,        0k used,  9936892k free,   670076k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
11825 root      20   0  201m  53m  31m R   17  1.0   2:02.60 Xorg                                                                                                                                                                            
11898 ghamlin   20   0  159m 7784 5720 S    6  0.1   0:58.41 gnome-session                                                                                                                                                                   
11932 ghamlin   20   0 24264 1584  600 S    6  0.0   0:51.72 dbus-daemon                                                                                                                                                                     
11935 ghamlin   20   0 59964 6388 2512 S    5  0.1   0:50.89 gconfd-2                                                                                                                                                                        
11964 ghamlin   20   0  288m  37m 9860 S    5  0.7   0:36.18 compiz                                                                                                                                                                          
19030 ghamlin   20   0  511m  59m  33m R    2  1.1   0:18.87 chromium-browse                                                                                                                                                                 
11941 ghamlin   20   0  308m  12m 8780 S    2  0.2   0:21.73 gnome-settings-                                                                                                                                                                 
 1326 ghamlin   20   0     0    0    0 Z    2  0.0   0:00.05 nautilus <defunct>                                                                                                                                                              
12796 ghamlin   20   0  227m  20m 9.9m S    2  0.4   0:13.63 python                                                                                                                                                                          
18120 ghamlin   20   0  236m  15m  10m S    2  0.3   0:02.28 gnome-terminal                                                                                                                                                                  
26441 ghamlin   20   0  858m  52m  32m S    2  1.0   0:09.93 chromium-browse                                                                                                                                                                 
 1328 ghamlin   20   0  194m 9348 7380 S    1  0.2   0:00.04 nautilus                                                                                                                                                                        
11961 ghamlin   20   0  264m  16m  11m S    1  0.3   0:14.10 gnome-panel                                                                                                                                                                     
11942 ghamlin   20   0  164m 8304 6440 S    1  0.2   0:08.70 gnome-power-man                                                                                                                                                                 
11969 ghamlin   20   0  160m 8244 6404 S    1  0.1   0:05.35 bluetooth-apple                                                                                                                                                                 
11988 ghamlin   20   0  371m  12m 9136 S    1  0.2   0:05.90 e-calendar-fact                                                                                                                                                                 
12014 ghamlin   20   0  280m  14m  11m S    1  0.3   0:05.06 clock-applet                                                                                                                                                                    
12015 ghamlin   20   0  269m  12m 9868 S    1  0.2   0:05.54 indicator-apple                                                                                                                                                                 
12022 ghamlin   20   0  293m 9968 7592 S    1  0.2   0:05.05 e-addressbook-f                                                                                                                                                                 
12031 ghamlin   20   0  137m 5496 4328 S    1  0.1   0:04.36 indicator-sessi                                                                                                                                                                 
12038 ghamlin   20   0  138m 5132 4052 S    1  0.1   0:07.74 indicator-me-se                                                                                                                                                                 
12051 ghamlin   20   0  132m 4856 3884 S    1  0.1   0:04.01 indicator-messa                                                                                                                                                                 
12153 ghamlin   20   0  160m 2884 1304 S    1  0.1   0:04.74 gnome-screensav                                                                                                                                                                 
 1112 ghamlin   20   0 19280 1336  948 R    0  0.0   0:00.03 top                                                                                                                                                                             
11821 root      20   0 80568 3472 2816 S    0  0.1   0:01.57 gdm-binary                                                                                                                                                                      
11880 ghamlin   20   0 73864 2884 2228 S    0  0.1   0:03.25 gnome-keyring-d                                                                                                                                                                 
11947 ghamlin   20   0 68436  18m 2020 S    0  0.3   0:04.99 gvfsd                                                                                                                                                                           
11957 ghamlin   20   0  267m  11m 8552 S    0  0.2   0:04.92 nm-applet                                                                                                                                                                       
11963 ghamlin   20   0  155m 6756 5296 S    0  0.1   0:02.26 polkit-gnome-au                                                                                                                                                                 
11972 ghamlin   20   0  263m  10m 8508 S    0  0.2   0:04.11 evolution-alarm                                                                                                                                                                 
12011 ghamlin   20   0  208m  12m 9444 S    0  0.2   0:01.68 wnck-applet                                                                                                                                                                     
12013 ghamlin   20   0  267m  13m  10m S    0  0.2   0:05.43 indicator-apple                                                                                                                                                                 
12055 ghamlin   20   0  223m 5564 4376 S    0  0.1   0:03.76 indicator-sound                                                                                                                                                                 
12057 ghamlin   20   0  125m 4316 3424 S    0  0.1   0:03.72 indicator-appli                                                                                                                                                                 
12090 ghamlin   20   0  132m  32m 4644 S    0  0.6   0:03.11 ubuntuone-syncd                                                                                                                                                                 
    1 root      20   0 23752 1928 1260 S    0  0.0   0:02.04 init                                                                                                                                                                            
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                                                                                        
    3 root      20   0     0    0    0 S    0  0.0   0:00.24 ksoftirqd/0                                                                                                                                                                     
    4 root      RT   0     0    0    0 S    0  0.0   0:00.02 migration/0                                                                                                                                                                     
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                                                                                                      
    6 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1                                                                                                                                                                     
    7 root      20   0     0    0    0 S    0  0.0   0:00.27 ksoftirqd/1                                                                                                                                                                     
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                                                                                                      
    9 root      20   0     0    0    0 S    0  0.0   0:00.06 events/0                                                                                                                                                                        
   10 root      20   0     0    0    0 S    0  0.0   0:00.09 events/1                                                                                                                                                                        
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                                                                                          
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                                                                                         
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns                                                                                                                                                                           
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr                                                                                                                                                                       
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                                                                                                                                                                              
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                                                                                                                     
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default
```


any ideas? cause im lost.

---

### Post by RJARRRPCGP on 2012-04-06
It wasn't even installed correctly! 

You must wipe the root partition, recreate the root partition, reinstall and try again. Sorry.

I may sound mean, but it's real clear that the installation is corrupted.

---

### Post by zombifier25 on 2012-04-07
Besides, why are you installing 10.10 now? Its support ends this very month!

---

### Post by LinuxFan999 on 2012-04-07
Ubuntu 12.04 will be released this month too, and will be supported for 5 years.

---

