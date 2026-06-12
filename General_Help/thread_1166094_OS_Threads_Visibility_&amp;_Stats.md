---
title: "OS Threads Visibility &amp; Stats"
date: 2009-05-21
forum: General Help
---

### Post by paddydd on 2009-05-21
Hi,

  Does Linux support OS Threads?

  Assuming the answer is yes, Is there a command line command like PS for Processes that shows the thread within a process? I would be interested in learning the CPU and memory usage for each thread within a process.

Thanks
Paddy

---

### Post by Legace on 2009-05-21
> **paddydd said:**
> Does Linux support OS Threads?

Do you mean Hyper-Threading? If so, yes.
You could try the **gnome-system-monitor** and the "Resources" tab, but I doubt that its what you're looking for..

---

### Post by wirelessmonkey on 2009-05-21
```

ps -auxf
top
htop

```

---

