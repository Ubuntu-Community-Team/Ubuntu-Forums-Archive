---
title: "Xorg extremely high memory usage in Jaunty (ATI  HD 3400)"
date: 2009-05-05
forum: Desktop Environments
---

### Post by hlxshady on 2009-05-05
Hello all,

I'm not sure if this is a problem at all since I didn't pay too much attention to this in 8.10.

I'm running 9.04 on T400 of lenovo, with fglrx switched on and compiz as well.
Despite the slow response of maximising windows, I found that the memory usage gets higher as the uptime gets longer.

With top, I can see that as followed (with uptime of 2:49)
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                
 3393 root      20   0  609m 292m  28m S   18  9.7  12:21.66 Xorg                                                                                                                   
 4301 stephen   20   0  434m 171m  34m R    9  5.7  11:17.60 firefox 

the xorg ate almost 1 G of memory (including Virtual memory).

And I think this is a bit absurd that the X is really a big eater ?

Could anybody tell me if this is normal or ... ?

---

### Post by s3lekta on 2009-05-07
> **hlxshady said:**
> Hello all,

I'm not sure if this is a problem at all since I didn't pay too much attention to this in 8.10.

I'm running 9.04 on T400 of lenovo, with fglrx switched on and compiz as well.
Despite the slow response of maximising windows, I found that the memory usage gets higher as the uptime gets longer.

With top, I can see that as followed (with uptime of 2:49)
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                
 3393 root      20   0  609m 292m  28m S   18  9.7  12:21.66 Xorg                                                                                                                   
 4301 stephen   20   0  434m 171m  34m R    9  5.7  11:17.60 firefox 

the xorg ate almost 1 G of memory (including Virtual memory).

And I think this is a bit absurd that the X is really a big eater ?

Could anybody tell me if this is normal or ... ?

problem has already been reported here --> [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186)

---

### Post by xianthax on 2009-07-09
that bug only looks to cover the min/maximize problems.

in regards to high Xorg memory usage, i have the same problem with an Nvidia card, Nvidia driver (newest from Nvidia), window manager makes no difference.  this is new for me in 9.04 and have tried various nvidia drivers.

after a day or two of up time xorg memory usage creeps its way through the roof and graphics operations begin getting very slow, video begins tearing, etc.

seems to occur faster, that is after less up time, when doing graphics intensive work, 3d apps, VM's in virtual box, etc.

top reports 2094m virt and 440m res for xorg as i type this.

---

