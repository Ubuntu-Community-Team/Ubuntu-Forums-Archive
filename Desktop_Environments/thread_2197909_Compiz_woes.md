---
title: "Compiz woes"
date: 2014-01-06
forum: Desktop Environments
---

### Post by mark98 on 2014-01-06
So what is compiz, what is it actually doing, why is it such a CPU hog?

Tasks: 242 total,   1 running, 241 sleeping,   0 stopped,   0 zombie
%Cpu(s): 36.7 us,  3.1 sy,  0.0 ni, 41.7 id, 18.5 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:   4047724 total,  3431476 used,   616248 free,   488200 buffers
KiB Swap:  4192928 total,    74292 used,  4118636 free,   763184 cached

  PID USER      PR  NI  VIRT  RES  SHR S  %CPU %MEM    TIME+  COMMAND                                 
 2611 mark      20   0 1862m 296m  19m S 237.4  7.5   1976:25 compiz                                 


I was planning on switching from Fedora to Ubuntu, but if taking 27 seconds for 'vi foo' to start it ain't gonna happen.  What is going on, what should I be looking at to get reasonable desktop performance?

(Yes, that is compiz using 237% of the CPU. )

System is a Dell SC1430.
root@fizzer:~# uname -a
Linux fizzer 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



I tried to do some searching on this topic, but nothing came up.  Just signed up to this forum, so maybe I'll get used to it eventually.

mjb.

---

### Post by deadflowr on 2014-01-06
Compiz in no way should have THAT high a cpu usage.
At worse, 25% is usually the highest I get.

Have you added any extra settings?

Looking it over isn't that a server build?
What kind of graphics card does it have?
Unity/compiz are extremely graphics reliant.

---

