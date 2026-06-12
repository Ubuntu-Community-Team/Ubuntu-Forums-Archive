---
title: "A way to see all running applications?"
date: 2009-05-04
forum: General Help
---

### Post by Fleshtone on 2009-05-04
Sometimes the system goes boggy and I want to know what is hogging the CPU.  In Windows, I'd start the task manager.  Is there an equivalent utility in Ubuntu?

---

### Post by michy99 on 2009-05-04
System->Administration->System Monitor

---

### Post by paradigm2 on 2009-05-04
> **michy99 said:**
> System->Administration->System Monitor

Just for knowledge, you may also run these in a terminal:

```

top

```

This will show the same info as system monitor and in my experience is more accurate.

```

sudo ps aux

```

This will show you a rudimentary list of all processes on the system.

---

### Post by Fleshtone on 2009-05-04
Thanks, the system monitor is prettier and more useful than MS's task manager.

---

### Post by oldos2er on 2009-05-04
htop

---

