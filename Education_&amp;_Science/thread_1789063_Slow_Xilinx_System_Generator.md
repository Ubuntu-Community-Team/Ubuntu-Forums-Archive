---
title: "Slow Xilinx System Generator"
date: 2011-06-23
forum: Education &amp; Science
---

### Post by tommpogg on 2011-06-23
Hi,

I am using Xilinx System Generator on a 64-bit PC running Ubuntu 10.10.

It works quite fine, but it takes too long to simulate any system due to the "initializing" time required by each component.

This topic is discussed in this forum:
[http://forums.xilinx.com/t5/DSP-Tools/System-Generator-works-very-slow-Why/td-p/21140/page/4](http://forums.xilinx.com/t5/DSP-Tools/System-Generator-works-very-slow-Why/td-p/21140/page/4)

Unfortunately, no definitive solution is provided. It seems that the problem is related to some writing permissions and to the caching of simulation files.

Does anyone know a way to speed up the "initializing" phase?

Thank you

---

### Post by tommpogg on 2011-06-30
I found a solution to speed up the "initializing" phase:

1) run sysgen (which implies that Matlab is started)
2) in the Matlab prompt type: [core, sg, usertemp] = XLCACHE('getpath')
The output should be something like
[INDENT]core =
/home/*username*/.Xilinx/Sysgen/sg_core_cache
sg =
/home/*username*/.Xilinx/Sysgen/lin64/cache5
usertemp =
/tmp/sysgentmp-*username*
[/INDENT]3) use chmod to turn on the writing permission on the folders (core, sg and usertemp)

Now, sysgen should run at normal speed

---

