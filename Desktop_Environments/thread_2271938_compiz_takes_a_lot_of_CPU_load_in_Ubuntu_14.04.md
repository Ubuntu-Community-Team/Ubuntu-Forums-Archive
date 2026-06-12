---
title: "compiz takes a lot of CPU load in Ubuntu 14.04"
date: 2015-04-02
forum: Desktop Environments
---

### Post by Bibrak on 2015-04-02
I have recently installed Ubuntu 14.04 and compiz takes a lot of CPU load. It was actually a bug reported in the following link

[https://bugs.launchpad.net/compiz/+bug/1293384](https://bugs.launchpad.net/compiz/+bug/1293384)

Here is my top:

 USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1306 root      20   0  490744 180152  19188 R  70.5  2.2   4:27.32 Xorg        
 2007 xx  20   0 1801232 306892  39900 S  64.9  3.8   4:17.83 compiz      
 2471 xx  20   0 1152992 378808  51304 S   5.3  4.7   0:49.49 firefox 

Do we have a solution for this these days?

---

### Post by grahammechanical on 2015-04-02
Are you running on llvmpipe? If not it is not the same bug. If you are running on llvmpipe then your video adapter is not capable of running Unity 3D because it cannot do 3D accelerated rendering in hardware. The CPU is having to do the work. Either that or there is a conflict with a proprietary video driver that is forcing Ubuntu to load using llvmpipe and instead of the proprietary video driver. That could be why there is such a load on the CPU.

I am using a development version of 15.04 on a machine with an Intel dual core CPU running at 2.40 GHz and 1 GB RAM. And Compiz is using less than 3% CPU and dropping to 0.3%. And never more that 10% RAM. 

Regards.

---

### Post by Bibrak on 2015-04-03
So I installed the drivers and it now works fine. The system load has been reduced.

---

