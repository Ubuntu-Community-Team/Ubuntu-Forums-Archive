---
title: "Is this ok?"
date: 2006-02-14
forum: Desktop Environments
---

### Post by andy5667 on 2006-02-14
I have the following cpu's. Will these be ok?
Intel Celeron D 2.53GHz LGA775
Intel Pentium D 3.4GHz LGA775
Intel Pentium 4 3.0GHz Socket 478

---

### Post by rado_london on 2006-02-14
I dont see any problems. You can even try 2 different kernels - 386 and 686- I prefer 386
Good Luck

---

### Post by taurus on 2006-02-14
Those are faster than most people have around here running Ubuntu!!!  ;)

---

### Post by mednamot on 2006-02-14
that's for sure - I can't remember what mine is, but I know it doesn't run in the GHz's

---

### Post by danish_demon on 2006-02-14
a quick question: i don't know/remember what speed my processor is at.  is there a quick way to find this out in ubuntu (a la my computer->properties in windows)?

---

### Post by taurus on 2006-02-14
cat /proc/cpuinfo

---

### Post by alfonz on 2006-02-14
[QUOTE=andy5667]I have the following cpu's. Will these be ok?
Intel Celeron D 2.53GHz LGA775
Intel Pentium D 3.4GHz LGA775
Intel Pentium 4 3.0GHz Socket 478[/QUOTE]

you might want to try the smp kernels with the pentiums I asume the p4 has HT and Pentium D is a dualie. Not sure how well smp will work on a Celeron hmmm....

---

### Post by Nasty Dollars on 2006-02-15
Normally it will work just fine.
I can advise you the 386, however if you run the default install, Ubuntu will choose the best Kernel for your system.

---

### Post by Lord Illidan on 2006-02-15
I thought that 686 was **optimised** for these kinds of processors, why use the 386???

---

### Post by taurus on 2006-02-15
[QUOTE=Nasty Dollars]Normally it will work just fine.
I can advise you the 386, however if you run the default install, Ubuntu will choose the best Kernel for your system.[/QUOTE]
I thought the CD only comes with one kernel and it's i386 so how does it choose the best kernel for your system?  You have to do that yourself after installing with either synaptic or apt-get!!!

---

