---
title: "Poor Memory Performance"
date: 2009-03-31
forum: General Help
---

### Post by jacoblyles on 2009-03-31
Without any user applications open, about 1.7 GB of my 2.5 GB of RAM are used. A look under "processes" in the system monitor reveals about 400 to 500 MB worth of processes running. What do the other 1.3 GB go to? Is this normal?

If I do work in a web browser, over time the RAM can fill completely up and the system starts to hang. 

Lastly, I could have sworn this computer had more memory than 2.5 gigs and I am running a 64 bit operating system. Does anyone know where my extra mem might be hiding?

Thanks.

---

### Post by jacoblyles on 2009-03-31
Also, I found out that I can fix this problem by rebooting. It seems that maybe Ubuntu just isn't releasing memory for dead programs. 

Is there a way to fix this? One of the reasons I left Windows is I got tired of constant reboots.

---

### Post by hyper_ch on 2009-03-31
unused ram = wasted ram

Stuff remains in cache even if its not needed anymore.

Ioen a terminal and run

```

free -mem

```
that will show you more accurate stats.

---

