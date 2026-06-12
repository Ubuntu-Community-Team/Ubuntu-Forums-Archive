---
title: "Finding which process was killed due to OOM"
date: 2009-03-08
forum: General Help
---

### Post by yang on 2009-03-08
When Linux runs out of memory (OOM), the OOM killer chooses a process to kill based on some heuristics.  How do I find out which processes were recently killed by the OOM killer?

---

### Post by snova on 2009-03-08
I don't know about a way to do it directly, but the OOM killer will log a message according to its source code:

[PHP]
printk(KERN_ERR "Killed process %d (%s)\n",
                task_pid_nr(p), p->comm);
[/PHP]

So if you grep dmesg afterwards:

```
dmesg | grep "Killed process"
```

You should turn up some results.

---

