---
title: "Ubuntu/Unity very slow to start"
date: 2014-02-27
forum: Desktop Environments
---

### Post by jacquelin-caron on 2014-02-27
I really don't understand the source of this problem. The main thing that is annoying is that Chrome (and even FireFox) are barely usable for like 10 minutes. I'm trying to reload some pages (3 of them), it takes forever.

Also, the dash board doesn't work during that same amount of time. I typed in something, and it keeps looking. I managed a couple of time to finally start Monitor during that long waiting period and the CPUs are barely used, internet connection is what I expect to be (which is almost not used). The only thing not laggy is the system updates. If there's some updates, I can install them during that time, everything works like it should.

I completely deactivated the "Record file and application usage" and the "include only results" when searching in the Dash.

Any ideas what's wrong with my setup?

---

### Post by Dreamer Fithp Apprentice on 2014-02-28
What are you comparing it to? In other words have you been running this same OS on this same hardware for a while and it just got slow recently? Or were you running something else and everything got like cold mollasses after you installed this? If it is the latter, then the answer is probably a lighter setup. Unity and Gnome 3 are reputed to be resource hogs. You might try Lubuntu. Personally, I use plain Openbox on Saucy, and the more I learn, the more I look at still lighter configurations, but Lubuntu is pretty good, and no trouble at all to install and configure. If you go that route and don't like the file manager, Pcmanfm, try thunar before you give up on Lubuntu.

---

### Post by jacquelin-caron on 2014-03-02
Thanks for the reply!

I installed this computer with 13.04! Everything worked fine at the beginning but it started to happen. Then, I upgraded to 13.10, at first, again, it was fine, but then, it started to slow down.

Also, my computer is quite recent. 8 cores, GeForce 660, 16gb of rams, boot partition (and installed apps (except games)) on SSD!

Hope this can help!

---

### Post by phidia on 2014-03-04
When your computer slows down, or is slow open a terminal and type "top" to see what is using your cpu cycles. Hope that helps.

---

### Post by Portaro on 2014-03-05
Firefox charges CPU, and if you use the browser with a big ammount of time and sites visit, many cookies and - cache empty your memory after time, Bleachbit (soft) and clean firefox with him  or clean the history cookies on the browser options can be help in this cases, Blachbit to clean cache is the most effective.

Also you can have problems with any theme or anithyng that starts with the new 13.10 config that forces the freezing of system.

Please like phidia wrote, put the result of top , and if possible free -m

---

### Post by jacquelin-caron on 2014-03-06
Here's what I got with top:

> top - 16:33:22 up 10 min,  2 users,  load average: 6.85, 4.91, 2.29
Tasks: 253 total,   2 running, 251 sleeping,   0 stopped,   0 zombie
%Cpu(s):  2.2 us,  0.5 sy,  0.0 ni, 72.0 id, 25.4 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  16392828 total,  1804380 used, 14588448 free,    79164 buffers
KiB Swap:  1973244 total,        0 used,  1973244 free,   619084 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND           
 1228 root      20   0  192m  62m  37m S   6.0  0.4   0:23.24 Xorg              
 2498 widgg     20   0 1052m 125m  47m S   6.0  0.8   0:15.50 chrome            
 2284 widgg     20   0 1332m 102m  57m S   4.0  0.6   0:12.47 compiz            
 2982 widgg     20   0  644m  18m  12m S   2.0  0.1   0:00.26 gnome-terminal    
 3026 widgg     20   0  939m  35m  14m S   1.7  0.2   0:00.05 chrome            
 2596 widgg     20   0 1032m 130m  23m S   1.0  0.8   0:05.19 chrome            
 2606 widgg     20   0 1022m 116m  22m S   1.0  0.7   0:02.68 chrome            
 2396 widgg     20   0  310m  11m 9096 S   0.7  0.1   0:00.43 gtk-window-deco   
   17 root      20   0     0    0    0 S   0.3  0.0   0:00.51 rcu_sched         
 2069 widgg     20   0  349m 6248 4960 S   0.3  0.0   0:00.04 hud-service       
 2081 widgg     20   0  565m  16m  11m S   0.3  0.1   0:00.59 unity-panel-ser   
 2622 widgg     20   0  997m  90m  23m S   0.3  0.6   0:01.69 chrome            
 2949 widgg     20   0  956m  42m  16m S   0.3  0.3   0:00.16 chrome            
    1 root      20   0 27220 3040 1416 S   0.0  0.0   0:00.77 init              
    2 root      20   0     0    0    0 S   0.0  0.0   0:00.00 kthreadd          
    3 root      20   0     0    0    0 S   0.0  0.0   0:00.00 ksoftirqd/0       
    4 root      20   0     0    0    0 S   0.0  0.0   0:00.17 kworker/0:0

Hope this could help

---

### Post by jacquelin-caron on 2014-03-08
One more detail I just noticed! After the last update, my NVidia driver was messed up... so I had to reinstall it. But when it was done, I logged in and start chrome. But chrome loaded fast (at the normal speed it's supposed to load). Is it possible that the WebGL stuff or any GPU settings are messing up with Chrome?

---

### Post by tjmackmer on 2014-03-09
htop is a great terminal utility for ubuntu. You can kill, change priority of processes, And view memory and cpu usage.
Evreything works quickley on my compaq presario CQ56

cpu: 2.2ghz
ram: 2gb
250gb hdd

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
> **jacquelin-caron said:**
> One more detail I just noticed! After the last update, my NVidia driver was messed up... so I had to reinstall it. But when it was done, I logged in and start chrome. But chrome loaded fast (at the normal speed it's supposed to load). Is it possible that the WebGL stuff or any GPU settings are messing up with Chrome?
That's plausible as far as I know. If it slows down again, I'd think about trying re-installing the driver again to see if it works. Another time I'd try purging chrome (after backing up any bookmarks, settings, etc.) and trying firefox for a while. If the problem only happens when you regularly run chrome for example,  at least you'd have a better idea where to look for the trouble. Also if it happens again it would be worth noting if a cold reboot cures it, even if only temporarlly. In addition to the cli utilities already mentioned by you and others, lxtask (like a gui top)  can be helpful along the same lines.

---

