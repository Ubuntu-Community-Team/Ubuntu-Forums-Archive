---
title: "Odd problem on swap......"
date: 2006-07-07
forum: Desktop Environments
---

### Post by Tails on 2006-07-07
Hi! My swap partition is mounted and activated, but the odd problem is that....... it is not being used at all.......

```

tails@tails:~$ free
            total       used       free     shared    buffers     cached
Mem:        903728     703808     199920          0      72420     339252
-/+ buffers/cache:     292136     611592
Swap:       104380          0     104380

```

is it normal???

Thanks!

---

### Post by ajgreeny on 2006-07-07
No problem at all with the large physical memory you have.  My system hardly ever uses swap either (I have 1Gb ram)

---

### Post by mcduck on 2006-07-07
By the way, I bet that you also have 1GB of RAM, and that you are running the default Ubuntu kernel (386).

You might want to install a kernel specific for your CPU, after that all your RAM will be recognised too. If you have a Pentium or other Intel CPU install package 'linux-686', or if you have Athlon or later AMD CPU install 'linux-k7' :)

---

### Post by Tails on 2006-07-07
> **ajgreeny said:**
> No problem at all with the large physical memory you have.  My system hardly ever uses swap either (I have 1Gb ram)

ah, ok... cheers.. thats good... :D


> **mcduck said:**
> By the way, I bet that you also have 1GB of RAM, and that you are running the default Ubuntu kernel (386).

You might want to install a kernel specific for your CPU, after that all your RAM will be recognised too. If you have a Pentium or other Intel CPU install package 'linux-686', or if you have Athlon or later AMD CPU install 'linux-k7' :)

actually, I am using linux-k7 kernel... :P and yes I have 1GB RAM, but the problem it isnt reconigise all 1GB RAM is because of ATI being crap on their graphics driver... lol... I couldnt use the sideport only mode for my graphics card, so, I have to use UMA and take 128MB RAM out of my RAM for it... lol.. >_<

---

