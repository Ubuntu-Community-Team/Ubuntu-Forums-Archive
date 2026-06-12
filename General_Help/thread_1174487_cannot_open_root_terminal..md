---
title: "cannot open root terminal."
date: 2009-05-31
forum: General Help
---

### Post by tactx on 2009-05-31
Click...cursor rotates and then nothing...??
any ideas?

---

### Post by anarchyinc on 2009-05-31
can you open a normal terminal and type su?

---

### Post by dcstar on 2009-05-31
> **tactx said:**
> Click...cursor rotates and then nothing...??
any ideas?

Known "bug" in 9.04 (there is no root terminal in 9.04 actually), change the launcher to this:

```
gnome-terminal -e "sudo -i"
```

---

### Post by tactx on 2009-05-31
Thanks bunches! :popcorn:

---

