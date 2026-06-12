---
title: "removing e17"
date: 2008-11-14
forum: Desktop Environments
---

### Post by malachi1990 on 2008-11-14
Can anyone tell me how to remove e17 from ubuntu?

---

### Post by taurus on 2008-11-14
How did you install it?  If you used either synaptic or apt-get, you can use the same process to remove it.

---

### Post by malachi1990 on 2008-11-14
If it had been in the repos, I would've done so.  But I had to install it by compiling from source.

---

### Post by taurus on 2008-11-14
Did you use "sudo make install" or "sudo checkinstall" to install it?

If you want to remove something that you have installed from source, you need to run

```
sudo make uninstall
```
from the same directory where you installed it to remove it.  Again, some programs don't have that option so you just have to read either README or INSTALL on how to remove it.

---

