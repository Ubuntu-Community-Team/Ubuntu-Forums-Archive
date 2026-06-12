---
title: "unrar issues"
date: 2008-12-15
forum: General Help
---

### Post by midna on 2008-12-15
I have a quad core q6600 and whenever I try to unrar anything, my computer is unusable until the unrar has finished. Firefox won't respond, amarok wont' respond, user tasks are interrupted. When running xp I can have a ton of unrars going and my computer is still usable. Same files, and I've tried both unrar and unrar-nonfree. 

What's going on here?

---

### Post by taurus on 2008-12-15
Are you running i686 or x86_64?

```
uname -a
free -m
```

---

### Post by midna on 2009-01-01
Sorry for the delay. Anyways heres the information you asked for. It is i686 and not 64bit. 

$ uname -a
Linux liquidsilk 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux

$ free -m
             total       used       free     shared    buffers     cached
Mem:          3545       3441        104          0         95       2651
-/+ buffers/cache:        694       2850
Swap:         9703          4       9698

---

### Post by Copernicus1234 on 2009-01-01
I had the same problem and fixed it by lowering the priority of the process.

So when you start a long unrar operation, go to a command prompt and type top to get the process id of the rar program. Then use renice to alter the priority of the process:

**renice +10 -p <process number>** (will set priority to +10, I think  -19 is the highest priority you can set and +20 is the lowest.)

---

### Post by midna on 2009-01-01
That would work, thank you for the suggestion, but I'm not going to manually renice every unrar. Especially when I have a quad core that should more than handle an unrar or two while I browse the web, type a paper, or do other menial tasks. In windows xp, this problem is nonexistant. 

I run ubuntu on my laptop and love it, but it doesn't seem to be quite ready to run typical desktop tasks quite yet.

---

