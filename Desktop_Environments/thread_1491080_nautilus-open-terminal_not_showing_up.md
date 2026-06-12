---
title: "nautilus-open-terminal not showing up"
date: 2010-05-23
forum: Desktop Environments
---

### Post by jomex on 2010-05-23
i just:

sudo apt-get install nautilus-open-terminal

but it doesn't show up in nautilus

when i do:

gksudo nautilus

and open the context menu, it does

how can i get the open-terminal to show up as user?

---

### Post by SlidingHorn on 2010-05-23
nautilus-open-terminal is, in fact in the repos -- i just did an apt-cache search for it.  if it's saying the package doesn't exist, I'd run a sudo apt-get update to re-check them

```
sudo apt-get update
sudo apt-get install nautilus-open-terminal
nautilus-open-terminal
```

(one @ a time)

---

### Post by jomex on 2010-05-23
the installation worked fine, the command just doesn't show up in nautilus

---

### Post by ingvildr on 2010-05-23
I think you have to log out/back in for it to show up.

---

### Post by jomex on 2010-05-24
works, thanks!

---

