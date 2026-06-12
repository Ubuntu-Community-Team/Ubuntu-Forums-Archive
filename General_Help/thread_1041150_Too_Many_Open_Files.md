---
title: "Too Many Open Files"
date: 2009-01-16
forum: General Help
---

### Post by Unparallelogram on 2009-01-16
In an essentially vanilla install of Ubuntu, something is consuming an unreasonable amount of file descriptors. In particular, Pidgin will sometimes give me a warning when I try to open a link that it cannot open a pipe to its child process as a result. Does anyone know what might cause this/how I could diagnose this further/what I can do? Thanks.

---

### Post by matey3 on 2009-01-16
sorry may be unrelated but...Do you run any anti virus by any chance like clamd. (we had almost the same problem and it was problem with clamd runing on the mail server).

I also see a lot of problems with "file descriptor error" when I boot one of those old machines, I have to ctrl c out of it (its like an endless loop)? I have not been able to find any solution for that one yet.
:(

---

### Post by Yashiro on 2009-01-16
> In an essentially vanilla install of Ubuntu
No tweaks or other apps? Never experienced this on any Ubuntu builds myself, yet. Are you sure it's not a Pidgin only issue?

---

### Post by khc on 2009-01-17
> **Unparallelogram said:**
> In an essentially vanilla install of Ubuntu, something is consuming an unreasonable amount of file descriptors. In particular, Pidgin will sometimes give me a warning when I try to open a link that it cannot open a pipe to its child process as a result. Does anyone know what might cause this/how I could diagnose this further/what I can do? Thanks.

I believe it's caused by a plugin, but unfortunately I don't remember which one off the top of my head.

---

