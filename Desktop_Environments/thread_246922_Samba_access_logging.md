---
title: "Samba access logging"
date: 2006-08-29
forum: Desktop Environments
---

### Post by seanUSXIII on 2006-08-29
Is there a program that can notify in real time (i.e. a little pop-up) when a user connects to a share through samba?

Thanks,
Sean

---

### Post by ayoli on 2006-08-30
I dunno an app like that with gui, but you can start with tailing the right log in a term:
```
tail -f /var/log/log_you_want_to_see 
```
that's an oldschoolbut working method.*
regards.

---

### Post by seanUSXIII on 2006-08-30
I meant something more like what an MSN does when someone new signs on, but triggered by a connection through samba

---

