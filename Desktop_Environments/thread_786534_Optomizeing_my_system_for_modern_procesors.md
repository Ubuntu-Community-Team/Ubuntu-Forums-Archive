---
title: "Optomizeing my system for modern procesors?"
date: 2008-05-08
forum: Desktop Environments
---

### Post by Lorenzo1985 on 2008-05-08
I'm under the impression that my standard install of Hardy will be optimised for fairly old school processors. 
If this is true what are the steps to optimise my hardy install for my more modern Pentium 4 (32 bit)?

---

### Post by ilrudie on 2008-05-08
Why would you assume Hardy is optimized for old processors?  Are you having performance issues?  I am running a Phenom x4 with no problems and I am not seeing performance issues?

---

### Post by Lorenzo1985 on 2008-05-08
It's not really an assumption I'm pretty sure ubuntu is compiled with the compiler switches for 386 architechtures rather than 686. You wont notice any problems on your exceeding high end system as your processor achitechture is certainly capable of doing everything an old 386 is. However those of us with older slower pc might notice some small performance benefits gained from utiliseing more of our processors clever features such as [mmx]("http://en.wikipedia.org/wiki/MMX") and [3Dnow]("http://en.wikipedia.org/wiki/3DNow%21").

This brainstorm idea and its various duplicates support this view:
[http://brainstorm.ubuntu.com/idea/1573/](http://brainstorm.ubuntu.com/idea/1573/)

---

### Post by ilrudie on 2008-05-08
I am running the generic kernel on a Pentium M laptop as well.  If I do a uname -a I see my kernel as being i686.  I would imagine you would see the same thing.  If you do cat /boot/config-2.6.24-16-generic for Hardy or cat /boot/config-2.6.22-16-generic for Feisty you can see all the options your kernel was compiled with.  What are you recommending should be changed?

Note:  Unless you know what options you are looking for you will want to increase the size of your scrollback buffer before cating the kernel options as there are quite a few of them.

---

### Post by sdennie on 2008-05-08
You could do things like build a custom kernel optimized for your architecture but, I really don't recommend it.  For normal desktop usage, recompiling the kernel or certain apps and building them with settings "more optimized" for your chip, will show essentially no performance benefit (at least not a detectable one).

---

