---
title: "Kernel Personality? What's that all about?"
date: 2009-05-13
forum: General Help
---

### Post by superbiskit on 2009-05-13
Despairing of getting a gclcvs package that works, I thought I could download the current cvs from savannah.gnu.org and build my own.
Hah!
My attempt to run 'configure' ends with this happy note:
checking for word order... little
checking for sbrk... yes
checking for ADDR_NO_RANDOMIZE constant... yes 40000
checking for personality(ADDR_NO_RANDOMIZE) support... no
checking that sbrk is (now) non-random... no
configure: error: Cannot build with randomized sbrk. Your options:
     - upgrade to a kernel/libc that knows about personality(ADDR_NO_RANDOMIZE)"
     - recompile your kernel with CONFIG_COMPAT_BRK (if it has that option)"
     - run sysctl kernel.randomize_va_space=0 before using gcl
------------

Now, the last suggestion I could do -- even set it in a startup script, I suppose.  I understand it is all about avoiding some exploits that depend on being able to predict where stuff might wind up in memory.  What other unintended consequences there may be, I don't know.

BUT, this is the first time I've had an application tell me I needed to reconfigure my kernel!  The Ubuntu and Debian teams must manage to build the beast with the distro kernels. [Yes?]

---

