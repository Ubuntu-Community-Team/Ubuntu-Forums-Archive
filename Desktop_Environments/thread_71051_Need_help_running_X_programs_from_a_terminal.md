---
title: "Need help running X programs from a terminal"
date: 2005-10-02
forum: Desktop Environments
---

### Post by bsoric on 2005-10-02
Hey,
I'm not sure how to word this question, and as a result I don't know if it has been asked before, so if someone has asked this, I apologize.

What I want to do is run an X program from cron, then directly after that starts, run another program. The problem is when I do something like:

* * * * * program1; program2

, program1 needs to finish running before program 2 starts.

I've worked out all other problems regarding running X programs from cron, but this last one is really starting to annoy me.

Thanks in advance,
Brett

---

### Post by cwaldbieser on 2005-10-02
[QUOTE=bsoric]Hey,
I'm not sure how to word this question, and as a result I don't know if it has been asked before, so if someone has asked this, I apologize.
What I want to do is run an X program from cron, then directly after that starts, run another program. The problem is when I do something like:
* * * * * program1; program2
, program1 needs to finish running before program 2 starts.
I've worked out all other problems regarding running X programs from cron, but this last one is really starting to annoy me.
Thanks in advance,
Brett[/QUOTE]
I am not sure if cron really handles the sequencing of programs.  However, you should be able to simply create a script that executes the programs in sequence, and then make the script a cron job.  E.g.
```

#! /bin/bash

#Runs 2 programs in sequence.
#Program 1 must finish before program 2 starts.
x-program1
x-program2

```

---

### Post by bsoric on 2005-10-02
What I wanted to do is run program2 while program1 was still running.
I got it working though. What worked was:

* * * * * program1 & >> /dev/null; program2

---

