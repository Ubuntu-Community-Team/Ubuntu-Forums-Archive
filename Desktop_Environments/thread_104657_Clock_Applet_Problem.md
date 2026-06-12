---
title: "Clock Applet Problem"
date: 2005-12-16
forum: Desktop Environments
---

### Post by PhilOSparta on 2005-12-16
I have an annoying clock applet problem.  The clock is running at double speed.
There are other threads that tell you how to fix this problem, BUT none of them have worked satisfactorily.   These include adding "noapictimer, noapic and nolapic" to the grub loader.  In my case, if the double clock problem is fixed, my internet access becomes very erratic. ( one second on one off. )

Other things I have tried:  
Using adjtimex -c  shows that the clock is running at 10000 ticks with a suggested 5000 ticks.   
Running  /usr/sbin/adjtimexconfig  provides an invalid argument to the kernel during the boot sequence.
The hardware clock is very accurate.  If I could get the clock applet to be driven from that, I would have no problems.

On several threads the OP with the problem just said he/she would live with it.    I would like to get it fixed.  It causes timestamps on email, file modifications etc to be set further in the future.  Just think of it.  I send you an email and you receive it before the time it was sent.   :rolleyes:  Could you live with that?:confused: 

Any suggestions would be appreciated.

---

