---
title: "System freezes"
date: 2006-02-14
forum: Desktop Environments
---

### Post by eMuNiX on 2006-02-14
Not sure whether to post this in software or networking.  Have had Kubuntu 5.10 installed since release basically and it has been fantastic up until last night.  Now the system freezes for a fraction of a second everyone 2-3 seconds.  The only thing that I have changed on my system is the router from a Conexant based item to an ADSL2/2+ unit, I’ll try changing back later but I doubt that this is the problem.  If I turn all the ‘extras’ off like SuperKaramba it makes no difference either.  How would I track down what is causing the freezing.  The machine is fine if I boot into XP, but I don’t fancy spending the next 3 hours updating it as it has been so long since I last booted to that OS.  Will also check if there is a problem under Xfce and Gnome later to see if it just a KDE issue or not.

---

### Post by eMuNiX on 2006-02-15
Darn Gnome works brilliant so there is something up with KDE that is doing this :(

---

### Post by eMuNiX on 2006-02-18
Seems that the gam_server is the culprit, this is 'top' from a KDE session:-
```

top - 13:16:03 up 2 min,  1 user,  load average: 5.32, 1.70, 0.60 
Tasks:  98 total,   2 running,  96 sleeping,   0 stopped,   0 zombie 
Cpu(s):  6.0% us, 41.0% sy,  0.0% ni, 53.0% id,  0.0% wa,  0.0% hi,  0.0% si 
Mem:    516320k total,   292620k used,   223700k free,    25296k buffers 
Swap:   104380k total,        0k used,   104380k free,   134080k cached 

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 9149 emunix    15   0  2460 1232  900 S 40.2  0.2   0:13.02 gam_server 
 9262 emunix    17   0 40028  20m  15m S  2.7  4.1   0:03.23 gaim 
 9147 emunix    17   0 33548  19m  15m S  2.0  3.9   0:02.17 kded 
 8844 root      16   0  150m  19m 2168 S  1.7  3.8   0:08.46 Xorg 
 9245 emunix    16   0 31484  17m  13m R  0.3  3.4   0:00.88 konsole 
 9258 emunix    15   0 38580  23m  17m S  0.3  4.6   0:01.64 konqueror 
 9364 emunix    17   0  2132 1092  844 R  0.3  0.2   0:00.04 top 
    1 root      16   0  1560  528  460 S  0.0  0.1   0:01.55 init 
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0 
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 events/0 
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper 
    5 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kthread 
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid 
   84 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0 
  110 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush 
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush 
  113 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0 
```

This is top from a Gnome session:-

```
top - 15:21:13 up 13 min,  1 user,  load average: 0.54, 0.74, 0.49 
Tasks:  83 total,   1 running,  82 sleeping,   0 stopped,   0 zombie 
Cpu(s):  9.3% us,  1.3% sy,  0.0% ni, 89.0% id,  0.0% wa,  0.3% hi,  0.0% si 
Mem:    516320k total,   489380k used,    26940k free,    42944k buffers 
Swap:   104380k total,        0k used,   104380k free,   165800k cached 

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 8725 root      15   0  202m  70m 6600 S  3.7 14.0   0:53.09 Xorg 
 9296 emunix    15   0  123m  60m  12m S  3.0 12.0   0:42.47 opera 
 9679 emunix    15   0 31000  16m  13m S  2.7  3.3   0:01.74 konsole 
 9320 emunix    15   0 74696  48m  17m S  1.0  9.7   0:38.90 python 
 8189 cupsys    16   0  6440 3504 1248 S  0.3  0.7   0:01.03 cupsd 
 9172 emunix    16   0 35380  16m  13m S  0.3  3.3   0:02.71 clock-applet 
 9712 emunix    16   0  2136 1088  844 R  0.3  0.2   0:00.04 top 
    1 root      16   0  1560  528  460 S  0.0  0.1   0:01.55 init 
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0 
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.07 events/0 
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper 
    5 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kthread 
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid 
   84 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 kblockd/0 
  110 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pdflush 
  111 root      15   0     0    0    0 S  0.0  0.0   0:00.14 pdflush 
  113 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0 
```

Note the abscence of gam_server.  So the question is what do I do to stop gam_server taking up so many resources.

---

### Post by eMuNiX on 2006-02-18
Tried updating gamin to the Dapper version. Tried adding noinotify into GRUB. None of these stop the freezing, stopping the process stops the freezing \\:D/

---

