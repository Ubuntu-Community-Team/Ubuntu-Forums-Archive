---
title: "Slow after upgrades"
date: 2006-06-21
forum: Desktop Environments
---

### Post by vav on 2006-06-21
I just did the latest upgrades to dapper, including kernel 2.6.15-25-686 #1 SMP PREEMPT, and the latest gnome. I reinstalled the ati fgrlx driver. 
There are two problems:
1> My system / user interface has slowed down. I see this in startup of programs and also in 3ddesktop performance.
2> There seems to be some problem with the sound. Google video sounds dont play, and I had to re-select XMMS, VLC sound channels to the default or hw(0,0) setting to get sound working after the upgrade.

Any pointers on how to fix the above?

Thanks,
--Vav

---

### Post by coe on 2006-06-21
There have been a whole bunch of threads complaining about this very issue, yet after weeks I still haven't seen any real solution proposed. 
cross fingers and keep updating... :( 

If you find out what causes the problems, please report back. 
good luck...

coe

---

### Post by kpkeerthi on 2006-06-21
Open terminal and type 'top' (without quotes) and let us know what your idle cpu usage is?

btw... What is your cpu? Is it dual core?

---

### Post by coe on 2006-06-22
Not to steal the OP's thread or anything... just curious myself  :) 

idling cpu: somewhere between 95% ~ 98%
(Intel pentium 4)

why?

---

### Post by kpkeerthi on 2006-06-22
Ooh... thats pretty high idle usage. The high idle cpu usage is affecting your system's responsiveness. But don't worry. I had similar problem after upgrading to i686 kernel but mine was idling at around 45%. I followed the instructions from here [http://www.ubuntuforums.org/showthread.php?t=194833](http://www.ubuntuforums.org/showthread.php?t=194833) and it fixed the issue. The SMP support enabled by default in the kernel is known to cause this problem on systems using single core CPUs like P4/P-M that have no need for that. My idle usage came down to 1% after applying the fix. Try it and let me know if it helped.

---

### Post by coe on 2006-06-22
Good tip, but it didn't seem to help in my case. idle cpu is still up there.
thanks though...
coe.

---

### Post by vav on 2006-06-22
I have a Pentium M 2GHz... so the SMP fix solved the issue! I had originally not posted my 'top' stats since the cpu usage rarely jumped above 25%. It did spike to upto 77% intermittently though. Thanks for the help!!
--Vav

---

### Post by vav on 2006-06-23
Do hyperthreading cpus qualify as SMP? In which case the fix is not required? This is for my home pc.

Thanks,
--Vav

---

