---
title: "Fix startup progtrams"
date: 2009-02-01
forum: General Help
---

### Post by dragos240 on 2009-02-01
Okay a while ago i wanted a non-gui ubuntu so i ran a command that removed startup programs so it goes into the tty terminal. I want it so iit logs into root automaticly and starts gdm, how do i do this?

EDIT: I found the command i ran:
```

sudo update-rc.d -f gdm remove

```also i ran this
```

sudo ln -s /etc/init.d/gdm /etc/rc2.d/K13gdm

```

---

### Post by dragos240 on 2009-02-01
Bump.

---

### Post by dragos240 on 2009-02-02
Bump

---

