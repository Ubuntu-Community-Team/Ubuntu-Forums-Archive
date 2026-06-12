---
title: "KDE slows down after some idling"
date: 2013-04-15
forum: Desktop Environments
---

### Post by wconstantine on 2013-04-15
I'm running KDE on Ubuntu 12.10 from the original repos. KDE slows down significtantly after a few hours of idling. I have a very powerful computer. 16 GB RAM, i5 processor, GTX 660 graphics card and an Intel SSD. Driver used is the on in the latest nvidia-current package. I have no idea what the problem can be. After I've used the system for some time after it has become slow from the idling, it starts getting faster and more snappier again. Anyone know what this can be?

$ free -m                                                                                                         
             total       used       free     shared    buffers     cached                                                             
Mem:         16032       6129       9902          0        162       4012                                                             
-/+ buffers/cache:       1954      14077                                                                                              
Swap:        16367          0      16367      

$ uptime                                                                                                          
 20:17:54 up  1:53,  2 users,  load average: 0.50, 0.63, 0.52 

$ sar -u 2 5
Linux 3.5.0-27-generic (fimbulwinter)   04/15/2013      _x86_64_        (4 CPU)

08:19:51 PM     CPU     %user     %nice   %system   %iowait    %steal     %idle
08:19:53 PM     all      4.63      0.00      0.63      0.00      0.00     94.74
08:19:55 PM     all      3.40      0.00      0.50      0.00      0.00     96.09
08:19:57 PM     all      4.11      0.00      0.87      0.00      0.00     95.01
08:19:59 PM     all      4.47      0.00      0.99      0.00      0.00     94.53
08:20:01 PM     all      4.03      0.00      0.50      0.00      0.00     95.47
Average:        all      4.13      0.00      0.70      0.00      0.00     95.17

---

### Post by oldos2er on 2013-04-16
Is it slowing from hard drive access? You can use **top** or **htop** to see which processes are consuming CPU cycles.

Do you have Nepomuk file indexing running? If so, try turning it off and see if it's better.

---

### Post by wconstantine on 2013-04-16
> **oldos2er said:**
> Is it slowing from hard drive access? You can use **top** or **htop** to see which processes are consuming CPU cycles.

Do you have Nepomuk file indexing running? If so, try turning it off and see if it's better.

iowait % from the sar output would be high if it were hard drive access I think. Also, the CPU usage is constantly low, so it's not really necessary to check which process is utilizing CPU. I will try turning off file indexing since I'm not using it. Thanks anyway.

---

### Post by dabl on 2013-04-16
It may be the scheduler (cfq is default) or the cpufreq control in the kernel, or both, or interactions between them.  You could try deadline or noop and see if it makes any difference.  In your BIOS you may have the option _not_ to let the OS control the CPU speed -- if so you might want to try it that way.  My Asus board has that.

The consequence of forcing it to run at its highest speed, of course, will be more energy consumption including when it is running and you aren't using it.

---

