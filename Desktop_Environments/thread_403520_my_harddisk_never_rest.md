---
title: "my harddisk never rest"
date: 2007-04-07
forum: Desktop Environments
---

### Post by zhangweiwu on 2007-04-07
Hello. I cannot remember when this begin to happen, maybe since the first day I installed xubuntu. It happens one day that I started System Load Monitor (an applet for XFCE) and noticed cpu usage is always 100%. Later I noticed my harddisk LED never stop flashing: it keep flashing since the machine boot, and never stop until the machine shut down.

Check top(1) it shows the system iowait is always between 85% to 99%, idle is always near 0%. uptime(1) shows system load is some 2.5. I think the machine is significantly slower then it should be because this Athlon 1.4GHz CPU cannot play Xvid movie, something I can do on a Pentium 700MHz CPU!

I think to myself there must be some process that keep using the harddisk, what is it? The memory usage (cache not included) is always below 80% so it cannot be the swap. For some time I think it's amuled but even if I killed amuled the system is still slow, still harddisk flashing and still iowait high.

Maybe there is a command letting me know which process is using the harddisk; maybe there are other reasons. What do you think?

zhangweiwu@eula:~$ uname -a
Linux eula.realss.com 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

---

### Post by MontanaMax on 2007-04-07
I have had good luck with the** htop** command to show each process and what it's doing to the machine. It's much easier to use than the traditional** top** command in my opinion.

if you don't have it installed already, it's in the universe repository.

sudo apt-get install htop

---

### Post by zhangweiwu on 2007-04-09
Thank you for providing hints on using htop. However my case is I do not know which process is keep using i/o (or using hdd) and htop is useful if you wish to know what a process is doing. Also I didn't find the field in htop about hdd usage yet, working on it.

---

