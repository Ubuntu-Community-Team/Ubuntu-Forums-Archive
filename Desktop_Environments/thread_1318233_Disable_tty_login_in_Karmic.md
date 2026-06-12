---
title: "Disable tty login in Karmic"
date: 2009-11-07
forum: Desktop Environments
---

### Post by shanix on 2009-11-07
It(Jaunty) used to be under /etc/event.d directory, but in Karmic, such folder does not exist.

Does anyone know a way to disable that??

---

### Post by Amgad elsaiegh on 2009-11-07
what is tty login ?

---

### Post by shanix on 2009-11-07
tty is the virtual console when you press Ctrl + Alt + F[1-6]

---

### Post by diesch on 2009-11-07
> **shanix said:**
> It(Jaunty) used to be under /etc/event.d directory, but in Karmic, such folder does not exist.

Does anyone know a way to disable that??

In karmic the upstart config files are in /etc/init/

---

### Post by Psumi on 2010-01-02
> **diesch said:**
> In karmic the upstart config files are in /etc/init/

So deleting them will remove the appropriate upstart entry?

---

### Post by diesch on 2010-01-02
Yes.

---

