---
title: "understanding data in 'top' display"
date: 2010-04-28
forum: Desktop Environments
---

### Post by chitowner2 on 2010-04-28
OK folks, this is a pretty simple question- for somebody. So pardon my ignorance, but here goes.

Why is it that when running 'top' in a shell and seeing it list say 8G available, 5G used, 3G free, that it seems impossible for the list of PID's to be using that much?

AFAICT, the top 20 or so PIDs (sorted for %MEM use) add up to maybe 1G or so, but 'free' corroborates that 5G are being used. Where are all the resource hogs I presume must be running? 

Chime in anybody.

CT
:confused:

---

### Post by conradin on 2010-04-28
ps -elf 

look for zombie processes (Z) in the S column. (second column over)
SZ Column is memory in KB look for processes with high memory usage there.

---

### Post by xebian on 2010-04-28
htop is better.

---

### Post by chitowner2 on 2010-04-28
Thanks Conradin. I normally just use ps -ef, so I tried adding the l and got a major zombie: /sbin/init (root) SZ=4893.

Xebian- Yes, Htop is definitely better. looks like more data and more user-friendly. Had to apt-get it, but now I see multiple copies of some apps, all with unique PID's and identical MEM & CPU usage. 

The replicate apps do not show as zombies with "ps -elf". Any idea why these show up with htop and not ps?

Thanks Guys
CT
:?

---

### Post by diesch on 2010-04-28
> **chitowner2 said:**
> 
Why is it that when running 'top' in a shell and seeing it list say 8G available, 5G used, 3G free, that it seems impossible for the list of PID's to be using that much?


Have a look at the values for "*buffers*" and "*cached*",  they are part of "*used*", too.

If you run "free" on the command line the "-/+ buffers/cache:" line shows you the memory used by programs (that is without *buffers* and *chached*)

---

