---
title: "[SOLVED] Chain flags in all cli programs?"
date: 2008-12-12
forum: General Help
---

### Post by chrispoole on 2008-12-12
I notice that with some CLI apps I can chain flags together.  

For example, with rsync, "-a -z -v" goes to "-azv". 

Is this a feature of most CLI programs, or just a few? (i.e., perhaps, is this something my shell, bash does?)

Thanks.

---

### Post by cariboo on 2008-12-12
Most programs allow you to chain flags, but if you are unsure, check the manpage for the particular program eg:

```
man rsync
```

Jim

---

### Post by chrispoole on 2008-12-12
Thanks; I was just wondering if this is a per-program type thing, or a shell thing, or maybe even an ncurses-type thing.

---

### Post by karlr42 on 2008-12-12
Generally per-program, it's more a convention than anything else.

---

### Post by Dr Small on 2008-12-12
It basically all boils down to the programmer, and whether he designed his program to allow chain options or not. Check the man pages if you are unsure.

---

### Post by chrispoole on 2008-12-12
Thanks all.

---

