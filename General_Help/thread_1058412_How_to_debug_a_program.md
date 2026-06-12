---
title: "How to debug a program?"
date: 2009-02-02
forum: General Help
---

### Post by rafaelsousa on 2009-02-02
I've installed Intrepid Ibex, and often (without no aparent cause), pidgin is closing.
There's a way I can run it, in order to I can figure out what's going on with that program?

Thanks

---

### Post by adamlau on 2009-02-02
Start Pidgin from a terminal and review the messages. Also, his should help get you started:

```
sudo apt-get strace
man strace
```

Else, build Pidgin with debugging flags enabled and review the messages in the debugging window.

---

