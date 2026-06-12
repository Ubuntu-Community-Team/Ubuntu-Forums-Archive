---
title: "$PATH ends: ' No such file or directory'"
date: 2009-03-28
forum: General Help
---

### Post by DavidDee on 2009-03-28
Hi:

I am new to Linux and just recently installed Ubuntu 8.10 (Intrepid Ibex) on my Lenovo 3000 V100 and am in the process of loading Resin, trying to figure out why the make utility can't find some files.

Anyway, my question is why does $PATH return the following right after I reboot?

bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory

The "No such file or directory" message is puzzling because every directory listed exists in my file structure. Is this a bug? Can I safely ignore this as a spurious message or does it mean something is wrong somewhere?

Thanks

daviddee

---

### Post by apmcd47 on 2009-03-28
Well, we'd need to see the line in question, but I'll bet you have something like ```
$PATH=...
```when you should have ```
PATH=...
``` in your .bashrc or .bash_profile file.

Andrew

---

### Post by dcstar on 2009-03-28
> **DavidDee said:**
> 
.......
Anyway, my question is why does $PATH return the following right after I reboot?

bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
.......

Because you do not just enter "$PATH" at a prompt - that is a command, you enter this to see the contents of the variable:

```
echo $PATH
```

---

### Post by DavidDee on 2009-03-29
> **dcstar said:**
> Because you do not just enter "$PATH" at a prompt - that is a command, you enter this to see the contents of the variable:

```
echo $PATH
```
Thank you David. A stupid beginer error that was confounding to me. Really appreciate it.

---

