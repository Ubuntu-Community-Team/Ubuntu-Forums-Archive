---
title: "Set CPU affinity?"
date: 2007-12-09
forum: Gaming &amp; Leisure
---

### Post by Hewure on 2007-12-09
Hi, I'm having a few dramas with UT in Gutsy.

I run a Q6600 Quadcore on a p35 Board, and Unreal GOTY is all over the place speedwise {it does the same in  XP, but I just set the affinty to 1 core in Task manager and it's sweet}.

Can i do this in Ubuntu - I should say can I do this easily!!! I'm sure there's a way, I tried Googling, but had no luck, apart from the TASKSET command, but how do I find the ID of UT {I had a bit of a look through Logs etc}.

Thanks

Steve

---

### Post by Vadi on 2007-12-09
If I understand you right:

System - Administration - System monitor. Find the process, right-click, and 'Change Priority'. And just drag the scrollbar.

---

### Post by Hewure on 2007-12-09
I'll give it a whirl...

---

### Post by Hewure on 2007-12-10
That killed it completely - won't even run now :-(

I'll re-install it and see what happens.

I don't want to change the PRIORITY, I just want the game to run on 1 core only, or it runs fast / slow all over the place as other cores are utilised.

UT came out in 1999, when Multi core CPU's were a pipedream.

---

### Post by Vadi on 2007-12-10
Oh.. well that involves some nifty commands which I don't know. A dualcore is still a pipedream to me.

---

### Post by stedevil on 2007-12-13
I just stumbled across this and the answer in my own search for how to set affinity so thought I'd spread the info. :)

To set CPU HARD affinity (as opposed to the soft affinity already done by the kernel automatically) install schedtool. Then read the manual to understand how it works.

The short version:

To set a process&#8217; affinity to only eg the first CPU (CPU0) and third CPU (CPU2) :

           #> schedtool -a 0,2 <PID>



Here is also a very good link to explain when and why HARD affinity could provide benefits vs SOFT affinity. I found way too many posts about "it's not needed" in my search instead of actual information, so clearing up the misconceptions might be a good thing in general. :)

[http://www-128.ibm.com/developerworks/linux/library/l-affinity.html](http://www-128.ibm.com/developerworks/linux/library/l-affinity.html)

---

