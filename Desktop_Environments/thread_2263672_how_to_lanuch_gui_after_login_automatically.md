---
title: "how to lanuch gui after login automatically"
date: 2015-02-02
forum: Desktop Environments
---

### Post by ip3t on 2015-02-02
hi,
i wander if ther is a way to boot in text mode (i've already edit the /ect/default/grub) and, once log in, starting the gui automatically.
my windows management is lightdm. i can start gui from terminal exec: sudo service lightdm start, but i must be the superuser to do this.

any advices?

thanks!

---

### Post by deadflowr on 2015-02-02
From a text session(console)
```
startx
```
no sudo needed, in fact don't even think of using sudo.

---

