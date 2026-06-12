---
title: "longer interruption"
date: 2007-03-29
forum: Desktop Environments
---

### Post by Senti on 2007-03-29
Hi,

i have a java programm that might not be interrupted for more than 5 seconds when running.

Sometimes ubuntu beginn to work with 100% cpu use (first iowait and then normal) and interrupt the programm for sometimes half a minute or more.

What can i do to avoid longer periods of interruption?

My system is ubuntu 6.06, pIII 700mhz, 256mb ram. 1gb swap.

Thanks :)

---

### Post by hde on 2007-03-30
You could try to run the program with a higher priority, se "man nice", how to set priority.

-20 is the most favourable and 19 is the least favourable. As I remember you have to use sudo to run it below 0.

---

