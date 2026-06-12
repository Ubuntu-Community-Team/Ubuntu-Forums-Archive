---
title: "Linux disto that supports suspention?"
date: 2009-10-19
forum: Desktop Environments
---

### Post by Eagles18 on 2009-10-19
I really love Ubuntu,but I just can't get my laptop to suspend or at least hibernate.This is a big deal-breaker for me.Does anyone know of any linux distro that will suspend without any problems?Or even better,how to get Ubuntu to suspend?
I've tried multiple distros,including Devian,Fedora,Open Suse,and some others.

Thanks in advance :guitar:

---

### Post by earthpigg on 2009-10-19
a couple things to look at in ubuntu...

is your swap partition significantly larger than the amount of ram you have? like, 2 or 3x as big.

and, have you tried playing with the power settings at all?

---

### Post by Eagles18 on 2009-10-19
> **earthpigg said:**
> a couple things to look at in ubuntu...

is your swap partition significantly larger than the amount of ram you have? like, 2 or 3x as big.

and, have you tried playing with the power settings at all?

My swap partition is the same size as my RAM,so I guess that could be a problem.BTW,is there a way to add more memory to my swap partition?

---

### Post by earthpigg on 2009-10-19
> **Eagles18 said:**
> My swap partition is the same size as my RAM,so I guess that could be a problem.BTW,is there a way to add more memory to my swap partition?

you will need to resize the partition from an ubuntu live cd using system -> admin -> partition editor.

if i was in your shoes, i'd do this just prior to a fresh install (since you are distro hopping on that computer anyways).

good partition scheme:

/ partition 15gb.
/swap partition a bit more than 2 times your RAM... if you have 1gb of ram, make swap 2.1gb.
/home partition for the rest.

---

### Post by diesch on 2009-10-19
> **Eagles18 said:**
> I really love Ubuntu,but I just can't get my laptop to suspend or at least hibernate.This is a big deal-breaker for me.Does anyone know of any linux distro that will suspend without any problems?Or even better,how to get Ubuntu to suspend?


[https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend) and [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume) may help

---

### Post by Eagles18 on 2009-10-19
I doubled my Swap memory and now I can hibernate.All I have to do is get my laptop to successfully suspend and my Ubuntu will be perfect.

---

