---
title: "installing ethernet card drivers"
date: 2006-07-19
forum: Desktop Environments
---

### Post by macogw on 2006-07-19
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

Using that page, I learned that my ethernet card's drivers are not in the computer.  I found the linux drivers online.  They're for version 2.4.13 and up, so I assume they should work.  I'm following the directions in the readme.txt file ([http://www.marvell.com/drivers/driverDisplay.do?dId=120&pId=36](http://www.marvell.com/drivers/driverDisplay.do?dId=120&pId=36)).  I'm sort of wondering if I should attempt this or wait til I get to school and ask someone who's been using Linux for a while to do it for me, but I started trying anyway.  I'm just not sure about the compiling thing.  The problem is it says "Check compiler (not found) [failed]" and "Check make (not found) [failed]" and "Check kernel gcc version (4.0.3) (Kernel:4.0.3 != gcc:729:) [failed]" then it tells me "There is a version mismatch between the compiler that was used to build the current running kernel and the compiler which you intend to compile the kernel module with.  In most cases, this is no problem, but there are cases in which this compiler mismatch leads to unexpected system crashes  If you know what you are doing and want to override this chec, you can do so by setting IGNORE_CC_MISMATCH system variable:
   Example: export IGNORE_CC_MISMATCH=1
Installation of sk98lin driver module failed


So, uh...what should I do?  Should I continue anyway or what?  Is there an easier way to install a driver?

---

### Post by Sendervictorius on 2006-07-19
You need to first install the "build-essential" package from synaptic. This package list will install all the components you need for compiling.

---

### Post by Ramses de Norre on 2006-07-19
Ok you don't want to start compiling a patched kernel, choose the Installation Mode and not the Patch Generation Mode.

You can post here if you get any error messages and when all is finished check the output of ls /proc/net/sk98lin/ to see whether the driver works (it should output your ethernet card name).

---

