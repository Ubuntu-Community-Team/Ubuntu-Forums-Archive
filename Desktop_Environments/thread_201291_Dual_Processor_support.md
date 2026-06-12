---
title: "Dual Processor support?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by rbgCODE on 2006-06-21
I have an old dual processor computer sitting around (dual 677 pentium 3's with a gig of ram)  Would ubuntu support both processors if I installed the server just text based version of it or what would I need to do to get it working?

---

### Post by lamego on 2006-06-21
You would need to install the kernel with SMP support:
```
sudo apt-get install kernel-image-`uname -r`-smp
```

---

### Post by rbgCODE on 2006-06-21
just install that and I am all set?

---

### Post by lamego on 2006-06-21
You are set about having a linux OS with multiprocessor support, if you want to do something usefull like serving pages or a database you have a lot more to do :p

---

### Post by MystaMax on 2006-06-21
yep. that should do it for you.  For a in depth look at what your trying to do, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=85917&highlight=kernel](http://ubuntuforums.org/showthread.php?t=85917&highlight=kernel)

---

