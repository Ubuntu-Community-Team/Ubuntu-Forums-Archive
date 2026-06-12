---
title: "Error starting Alien Swarm and Red Orchestra mods for UT2004"
date: 2006-11-19
forum: Gaming &amp; Leisure
---

### Post by zgerrz on 2006-11-19
I am trying to launch these two mods for UT2004, Alien Swarm and Red Orchestra, but I keep getting errors and I don't know exactly what they mean. I have installed the FragOps mod and it works perfectly. Here's what I get when I try to run these games from the console:

```
zgerrz@edgy:~$ alienswarm 
/usr/local/bin/alienswarm: 34: Syntax error: Bad substitution
zgerrz@edgy:~$ redorchestra 
/usr/local/bin/redorchestra: 29: Syntax error: Bad substitution
zgerrz@edgy:~$ 
```

I'm using the loki installers.

---

### Post by zgerrz on 2006-11-20
Nobody knows?

---

### Post by qrm on 2006-11-20
try commenting that line out (or the small section) in /usr/bin/alienswarm or /usr/bin/redorchestra . it helped me getting racer and others running

---

### Post by zgerrz on 2006-11-20
thanks, that did the trick

---

