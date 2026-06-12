---
title: "pkill or skill question"
date: 2009-02-26
forum: Desktop Environments
---

### Post by anystupidname on 2009-02-26
So lets say I'm sshed into a remote linux machine and I see via "who" that there are 12 root sessions open. I want to kill them all but don't want to lose the ability to ssh back in. pkill -u root will kill sshd, right? skill doesn't seem to have an option for me either. Is there a different command or a way to exclude just a single process from the slaughter?

Thanks!

---

### Post by anystupidname on 2009-04-27
anybody?!?

---

### Post by kanikilu on 2009-04-27
Since pkill can use regular expressions as the pattern, I think something like this would work: ```
pkill -u root [^sshd]
``` I think that should kill all processes owned by root that don't have "sshd" in the name - although I haven't tried it myself, because to be honest, I can't imagine a situation where this would be desirable...

---

### Post by sasha1024 on 2012-07-24
> pkill -u root [^sshd]

A-ha-ha. This will kill allmost all processes whose name contain any non-s, non-h and non-d letter. I.e. amlost all processes.

---

### Post by wildmanne39 on 2012-07-25
Thanks for sharing. Thread Closed.

---

