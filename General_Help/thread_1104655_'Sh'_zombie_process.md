---
title: "'Sh' zombie process"
date: 2009-03-23
forum: General Help
---

### Post by trepid666 on 2009-03-23
Hi, 

So I have a zombie process of Sh that appears almost right after gnome starts up. It doesn't give me any info on it. How would I go about tracing and fixing this?

Also, I try killing it in "top" to no avail. The PID keeps changing too.

---

### Post by kerry_s on 2009-03-23
"sh" is usually created from programs that are started without a "&" on the end, so what do you have in your session startup?

---

### Post by trepid666 on 2009-03-24
I just added some screenlets to my startup.

So I guess I should start there and maybe see which one is creating that zombie. Is there anyway to fix it or should I just not use that screenlet anymore?

---

### Post by kerry_s on 2009-03-24
> **trepid666 said:**
> I just added some screenlets to my startup.

So I guess I should start there and maybe see which one is creating that zombie. Is there anyway to fix it or should I just not use that screenlet anymore?

i think you just have to add "&" to the end or put "exec" in front of the command.
startup examples:
**screenlet &**
or
**exec screenlet**

see which 1 works for ya

---

### Post by kpatz on 2009-03-24
Do a ps -f on it to see what its full command line is.  That might help you trace it down.

One (or a small number of) zombie process isn't a problem.  If you see a ton of them, then it's time to do something.

---

### Post by trepid666 on 2009-03-24
This is the output:

```
master@master-laptop:~$ ps -f 20042
UID        PID  PPID  C STIME TTY      STAT   TIME CMD
master   20042 10016  0 14:06 ?        Z      0:00 [sh] <defunct>

```

The PID changes all the time and sometimes the zombie disappears... I just found it a little strange.

Thanks for the replies

---

