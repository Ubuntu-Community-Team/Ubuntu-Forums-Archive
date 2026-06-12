---
title: "change console prompt"
date: 2008-01-26
forum: Desktop Environments
---

### Post by kornelix on 2008-01-26
I want to change the console prompt to something shorter.

If I do this interactively, it works as expected:
export PS1="$: "

If I add this same line at the end of /etc/bash.bashrc,
it does nothing (old prompt remains).

---

### Post by taurus on 2008-01-26
Try adding it to ~/.bashrc.

When you are done, run

```
source ~/.bashrc
```

---

### Post by kornelix on 2008-01-26
Thanks, that works fine. 

Still wondering why my mod to /etc/bash.bashrc was being ignored.

---

