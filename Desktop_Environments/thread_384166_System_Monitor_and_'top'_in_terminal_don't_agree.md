---
title: "System Monitor and 'top' in terminal don't agree"
date: 2007-03-14
forum: Desktop Environments
---

### Post by caspermyboy on 2007-03-14
I'm running edgy and when comparing the output from the Gnome System Monitor to the 'top' command running in a terminal the results don't match.

System Monitor in the Memory and Swap History section on the Resource tab reports:
User Memory: 180.8 MiB of 995.5 MiB 18.1%
Used Swap:    0 bytes     of 203.9 MiB 0.0%

and running 'top' in a terminal reports:
Mem:   1023480k total,   510964k used,   512516k free,    80548k buffers
Swap:   208804k total,        0k used,   208804k free,   245172k cached

Now everything baring the amount of memory used seems to add up - any ideas why System Monitor thinks I'm using less than half the memory 'top' reports I'm using?

Quick second question why 'MiB' rather than 'MB' in the System Monitor.

Thanks in advance.

---

### Post by ComplexNumber on 2007-03-14
> any ideas why System Monitor thinks I'm using less than half the memory 'top' reports I'm using?
i seem to remember hearing that system monitor doesn't include cached memory. something like that anyway.


>  why 'MiB' rather than 'MB' in the System Monitor.
they're both the same , just different 'internationalisations'. i also think that they have slightly different definitions in 1 or 2 contexts.

---

### Post by mcduck on 2007-03-14
> **ComplexNumber said:**
> i seem to remember hearing that system monitor doesn't include cached memory. something like that anyway.



they're both the same , just different 'internationalisations'. i also think that they have slightly different definitions in 1 or 2 contexts.
First answer is right, second one is not  :)

MiB (and KiB) is the 'true' number, MB is what hard drive manufacturers use (the old 1024 vs 1000 difference).

So 1 MiB is 1024 KiB or 1048576 B (2^20), while 1MB is 1000KB or 1000000 B (10^6). This has been the official standard since end of 1998 (I'm not using it though, since the new MB has nothing to do with how your computer uses the disk or memory space, it only gives bigger numbers to print on hardware boxes).

---

### Post by ComplexNumber on 2007-03-14
> **mcduck said:**
> First answer is right, second one is not  :)

MiB (and KiB) is the 'true' number, MB is what hard drive manufacturers use (the old 1024 vs 1000 difference).

So 1 MiB is 1024 KiB or 1048576 B (2^20), while 1MB is 1000KB or 1000000 B (10^6). This has been the official standard since end of 1998 (I'm not using it though, since the new MB has nothing to do with how your computer uses the disk or memory space, it only gives bigger numbers to print on hardware boxes).
in other words, i'm right about the 2nd as well ;). i know what they both are.

---

### Post by mcduck on 2007-03-14
> **ComplexNumber said:**
> in other words, i'm right about the 2nd as well ;). i know what they both are.

Well, in a way yes, and then again no. As MiB and MB are not the same thing ;)

If you follow the standard you should pretty much stop using MB and use MiB instead. Using MB is in most cases incorrect.

---

### Post by ComplexNumber on 2007-03-14
they are often used interchangably. its only if one wants to be strict about everything that they differ.

---

