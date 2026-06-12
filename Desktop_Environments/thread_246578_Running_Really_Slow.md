---
title: "Running Really Slow"
date: 2006-08-29
forum: Desktop Environments
---

### Post by Vyizis on 2006-08-29
I have just installed ubuntu on my desktop PC again which has the following specs.

AMD xp2500+
Abit NF7 Nforce2 mb
ATI Radeon 9500pro

The problem is once i log on to the system it absolutely crawls, it takes about 20mins to get to the desktop screen. I have installed ubuntu on this machine before and i didnt get this problem and nothing has changed with the computer.

Anybody have any ideas?

---

### Post by lagagnon on 2006-08-29
Check output of the following command line commands to determine where your problem lies:

top (check wqhich processes comsume CPU)
free (check your RAM, see if using or if you have swap)
ps aux (to check all processes to see which might be using too much memory)

---

### Post by Vyizis on 2006-08-29
its nothing like that, i have loads of ram free, no swap space used and my cpu is not maxed out.

---

### Post by Vyizis on 2006-08-29
Ok i have fixed it now, i upgraded the kernal to the new k7 one and that seems to have solved the problem.

---

### Post by Vyizis on 2006-08-29
Ok i have fixed it now, i upgraded the kernal to the new k7 one and that seems to have solved the problem.

---

