---
title: "Excessive memory useage"
date: 2005-07-13
forum: Desktop Environments
---

### Post by eMuNiX on 2005-07-13
I have a P4 1500 with 512 RDRAM, most distros run great on this spec but for some reason Kubuntu is using all of the RAM.   How do I find which process is doing this?

---

### Post by dave9191 on 2005-07-13
You should generally use all of the RAM that your computer has. Linux caches files from the hdd into avaible ram space to speed up access to them. If you run 'top' into the command line it will give you a memory breakdown at the top. 

Mem:    515852k total,   494036k used,    21816k free,   214156k buffers
Swap:   522072k total,        0k used,   522072k free,    83916k cached


494mb are used, but take the buffers and cached mem away from that and Im only using just under 200mb ram. As more programs need to be put into the ram, the mem is allocated to them from the cached/ buffered files.

You should only be worried if the buffers and cache are low and your ram is totally used. 

Hope this helps.  

Dave

---

### Post by eMuNiX on 2005-07-13
only worried as I tried to play Q3A the other day with all SuperKaramba candy off and it was still choppy every 30 seconds, only seems to have happened since installing Gnome, WindowMaker and XFCE4 even though they are not running.

---

### Post by eMuNiX on 2005-07-13
top - 22:57:00 up  1:42,  2 users,  load average: 0.22, 0.05, 0.10
Tasks:  67 total,   1 running,  66 sleeping,   0 stopped,   0 zombie
Cpu(s): 14.2% us,  2.6% sy,  0.0% ni, 82.8% id,  0.0% wa,  0.3% hi,  0.0% si
Mem:    516364k total,   509460k used,     6904k free,    50216k buffers
Swap:   104380k total,        0k used,   104380k free,   244584k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7338 root      15   0 47040  33m 1920 S 12.0  6.6  12:20.69 Xorg
 7687 emunix    15   0 32700  19m  14m S  2.3  3.8   2:27.26 superkaramba
 7693 emunix    15   0 31820  18m  14m S  0.7  3.6   1:03.35 superkaramba
 9486 emunix    15   0 29240  15m  11m S  0.7  3.1   0:00.76 konsole
 7635 emunix    15   0  3044 1728  848 S  0.3  0.3   0:13.32 gam_server
 7649 emunix    16   0 26868  13m  10m S  0.3  2.8   0:03.62 kwin
 7651 emunix    16   0 28704  16m  12m S  0.3  3.3   0:03.72 kdesktop
 7653 emunix    15   0 31264  19m  14m S  0.3  3.8   0:22.43 kicker
 7673 emunix    15   0 90064  53m  10m S  0.3 10.6   1:53.46 opera
 9498 root      16   0  2080 1040  824 R  0.3  0.2   0:00.06 top
    1 root      16   0  1552  508  444 S  0.0  0.1   0:00.51 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0
    3 root       5 -10     0    0    0 S  0.0  0.0   0:00.01 events/0
    4 root       8 -10     0    0    0 S  0.0  0.0   0:00.02 khelper
   16 root      15 -10     0    0    0 S  0.0  0.0   0:00.00 kacpid
   98 root       5 -10     0    0    0 S  0.0  0.0   0:00.25 kblockd/0
  132 root      15   0     0    0    0 S  0.0  0.0   0:00.19 pdflush

With SuperKaramba off it is still the same and Q3A is as choppy as hell

---

### Post by dave9191 on 2005-07-13
That mem usage looks good, but you might want to direct your attention to config files that may have been altered when installing the window managers. They could have "tweaked" your X config files or something. 

Dave

---

### Post by GoldBuggie on 2005-07-14
Have you installed the correct drivers for your graphics card?

---

### Post by Gezzer on 2005-07-14
have u tried installing the
2.6.10-5 i686 kernel for the P processor ...

---

