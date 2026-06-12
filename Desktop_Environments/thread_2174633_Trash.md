---
title: "Trash"
date: 2013-09-15
forum: Desktop Environments
---

### Post by Henk_Kirchner on 2013-09-15
My trash can won't empty on command. Anyone experiecend the same problem?

---

### Post by codemaniac on 2013-09-15
The trash files are located under ~/.local/share/Trash/files/

You can empty trash with the below command.

```
rm -rf ~/.local/share/Trash/files/*
```

---

