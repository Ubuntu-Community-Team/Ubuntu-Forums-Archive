---
title: "How can i find my window manager?"
date: 2010-04-05
forum: Desktop Environments
---

### Post by kumaraSrlk on 2010-04-05
How can i find my window manager's name? I'm using kubuntu 9.10.

---

### Post by kellemes on 2010-04-05
kwin

---

### Post by 3Miro on 2010-04-05
> **kumaraSrlk said:**
> How can i find my window manager's name? I'm using kubuntu 9.10.

Unless you have installed something else, it is Kwin. It is possible that you have installed compiz by mistake. You can check if compiz is running by:

```
ps -e | grep compiz
```

If it doesn't return anything compiz is not working. You can also use the system task manager to see what processes are running.

---

### Post by shaka_zulu on 2010-04-05
Yes, your window manager is probably Kwin by default. If you didn't install compiz then KWin is the one you use.

---

