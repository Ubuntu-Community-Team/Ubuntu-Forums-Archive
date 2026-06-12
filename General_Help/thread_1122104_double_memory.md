---
title: "double memory"
date: 2009-04-10
forum: General Help
---

### Post by Doug11 on 2009-04-10
I just upgraded my RAM. I doubled the amount. Is there a way or command I can use to make sure my system is recognizing it all?

---

### Post by maheshasolkar on 2009-04-10
If you run:

```
  top
```

in the terminal, it will show you current memory in the header. Something like this:

```
top - 14:45:35 up 3 days, 16:01,  2 users,  load average: 0.19, 0.33, 0.77
Tasks: 171 total,   4 running, 167 sleeping,   0 stopped,   0 zombie
Cpu(s):  9.2%us,  3.1%sy,  0.0%ni, 87.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
**[COLOR="DarkRed"]Mem:   2072264k total,  1972320k used,    99944k free,   160600k buffers[/COLOR]**
Swap:  4192924k total,     4856k used,  4188068k free,  1154648k cached
```

---

### Post by Thura on 2009-04-10
```

cat /proc/meminfo

```

---

