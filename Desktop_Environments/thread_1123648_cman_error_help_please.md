---
title: "cman error help please"
date: 2009-04-12
forum: Desktop Environments
---

### Post by rick20 on 2009-04-12
cman error
when i log into 'Linux Ubuntu' i get this set of errors:
...

dlm_controld [4533]: cman_admin_init error 2

gfs_controld [4337]: cman_admin_init error 2

fence_tool: waiting for cman to start
fence_tool: waiting for cman to start
fence_tool: waiting for cman to start

unable to connect t cluster infrastructure after 30 seconds

unable to connect t cluster infrastructure after 60 seconds

unable to connect t cluster infrastructure after 90 seconds

can any1 help me get past this because it cant log into ubuntu anyway including recovery mode

---

### Post by PacSci on 2009-04-12
This seems like a kernel issue. What I can conclude from a bit of Googled research is that the kernel's cluster manager isn't starting for some reason, and thus the parts of the kernel in charge of handling distributed filesystems are not loading. 

No idea how to fix it - it doesn't seem like this is a very common problem - but my suggestion is to reinstall everything. Boot into a Live CD to recover any documents you might have, then start over.

BTW, it's Ubuntu Linux (or just Ubuntu), not Linux Ubuntu.

---

### Post by rick20 on 2009-04-14
cheers for the advice...will install Ubuntu Linux now :D lol

---

