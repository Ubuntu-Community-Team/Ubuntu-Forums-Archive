---
title: "iDesk?"
date: 2005-04-12
forum: Desktop Environments
---

### Post by telmo on 2005-04-12
I'm using XFCE4 and i tried installing idesk so i can have icons on my desktop, but i get this error:

```
Can't find config file or missing 'Config' table in the config file.
```

Can someone tell me wat's going on please? How do i install idesk?

---

### Post by remmelt on 2005-04-12
iDesk is pesky like that. If you don't give it the right files and folders, it won't run. I think .idesk.conf and .idesktop should be in your ~, plus there needs to be at least one icon configured. Stupid stuff, it won't create its own cfgs!

It segfaulted on me, I removed it.

---

### Post by chem415 on 2005-11-15
Hi, 

I had the same problem. I had to create a ~/.ideskrc and a ~/.idesktop directory. You put your images and *.lnk files in the ~/.idesktop directory. For a example of a ~/.ideskrc, check out the man page for idesk.  I unfortunaly ran in to another problem, now idesk Seg faults on me. 

HTH, 

chem415

---

