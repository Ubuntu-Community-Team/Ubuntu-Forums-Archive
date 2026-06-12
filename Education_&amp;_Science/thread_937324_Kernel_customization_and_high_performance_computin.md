---
title: "Kernel customization and high performance computing"
date: 2008-10-03
forum: Education &amp; Science
---

### Post by Lucrezia on 2008-10-03
Hello!


I'm a mathematician who usually run custom C code or matlab code (or both) for solving academic problems. My usual problem is typically performance-bound, which means that it is small enough to stay in the ram, but big enough to take anywhere from 18 hours to a week of continuous work to compute a solution.

Recently someone make me notice that i could save some time by running my code on a 64 bit distro rather than my usual ubuntu desktop, therefore it triggered curiosity in me, and I started looking on the web for more infos. The most interesting piece of work I've found on the web is this one:

[http://www.iit.bas.bg/PECR/56/78-85.pdf](http://www.iit.bas.bg/PECR/56/78-85.pdf)

Although old, it has made me think that maybe a custom kernel would be able to reduce my computing time. The improvements are quite small, and they wouldn't be noticed in a daily use, where problems are usually memory-bound (the cpu sleep most of the time) or dimensional-bound (p2p), but even a 1% improvement would be noticeable on a 7 days long computation. 

From my poor understanding of kernel architecture, I deduced that I have two possible path to improve my performance:

a) By customizing the kernel, removing useless module, but it basically would just reduce my start up time or free some ram space. Useful, but not dramatic.

b) By compiling the kernel using an intel compiler (on my Q6600 cpu) rather than GCC.


Anyone has some data on possible improvements? Any direct experience?
If i were to do this, would i have to expect any instability/incompatibility/any kind of issue?

---

