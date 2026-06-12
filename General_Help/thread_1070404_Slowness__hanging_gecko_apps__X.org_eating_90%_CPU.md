---
title: "Slowness / hanging gecko apps / X.org eating 90% CPU"
date: 2009-02-15
forum: General Help
---

### Post by Arjunanda on 2009-02-15
Hello folks,

My Ubuntu has got sick and is suffering some chronic disease. ;)

First, my Firefox became very slow, specially with gmail, youtube and facebook. Eariler, I was happily having more than ten tabs open at a time, but now five tabs seems to be too much, if gmail or facebook is open. Flash performance is really poor, cannot watch any youtube videos on this pc, as it will eat up all CPU practically freezing the desktop, and I need to do kill it with ctrl+alt+backspace.

Later also X.org started eating CPU time. And now I am quite stuck with this situation. I would like to solve the issue without re-installing the entire system.

I'm running Ubuntu 8.10, and have gradually distr-upgraded from 6.04 (if I remember correctly) as the upgrades have become available and the major flaws have got fixed.

---

### Post by Arjunanda on 2009-02-15
Installed Firefox 3.1b2 - and it seem to have solved the whole issue! Highly recommended!

---

### Post by Arjunanda on 2009-02-15
It did not solve the problem. Xorg still eats 75% of the cpu. But CPU load of firefox went down considerably.

Any ideas what may cause the behavior of Xorg?

```

user@ananda:~$ top

top - 16:15:56 up  5:39,  3 users,  load average: 1.97, 1.36, 1.06
Tasks: 126 total,   3 running, 123 sleeping,   0 stopped,   0 zombie
Cpu(s): 75.8%us, 19.1%sy,  0.0%ni,  0.0%id,  0.0%wa,  5.1%hi,  0.0%si,  0.0%st
Mem:   1284088k total,   892964k used,   391124k free,    39840k buffers
Swap:  1590424k total,    10764k used,  1579660k free,   403184k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
20529 root      20   0  295m  28m 8316 S 38.8  2.3   0:38.79 Xorg               
21140 user      20   0  300m 109m  27m R 17.1  8.8   0:55.39 firefox-bin        
21242 user      20   0  102m  23m  13m R 15.0  1.9   0:03.58 gnome-terminal     
20896 user      20   0 78064  34m  12m S 11.4  2.7   0:14.58 skype              
20799 user      20   0 13768 4552 3588 S  4.8  0.4   0:01.58 at-spi-registry    
 4797 chipcard  20   0  4660 1224  928 S  3.9  0.1   3:18.04 chipcardd4         
 4873 haldaemo  20   0  6316 2888 2260 S  3.3  0.2   1:09.28 hald               
21267 user      20   0  2416 1148  876 R  3.0  0.1   0:02.84 top                
20863 user      20   0 22436 9428 7716 S  1.2  0.7   0:00.88 multiload-apple    
 1266 root      15  -5     0    0    0 S  0.6  0.0   0:06.60 ata/0              
 1770 root      15  -5     0    0    0 S  0.6  0.0   0:11.56 scsi_eh_0          
 2638 root      15  -5     0    0    0 S  0.6  0.0   0:12.50 b43                
 4988 root      20   0  3440 1040  888 S  0.6  0.1   0:13.68 hald-addon-stor    
20780 user      20   0  8208 5116 2276 S  0.6  0.4   0:00.98 gconfd-2           
20806 user      20   0 23684  14m 9580 S  0.6  1.2   0:01.58 metacity           
20856 user      20   0 22324 3320 1804 S  0.6  0.3   0:01.10 gnome-screensav    
    1 root      20   0  1740  536  456 S  0.0  0.0   0:01.50 init               

```

---

