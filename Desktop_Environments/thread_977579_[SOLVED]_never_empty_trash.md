---
title: "[SOLVED] never empty trash"
date: 2008-11-10
forum: Desktop Environments
---

### Post by c/Kr3t on 2008-11-10
Whenever I go to empty my trash bin, there is always files left in there.  No matter how many times I try to empty it they never go away.

I've tried going to the trash directory with sudo nautilus but that always says that it cannot access it, directory doesn't exist.

---

### Post by aged hippy on 2008-11-10
I had this problem with the Kubuntu waste-bin, after differing advice and many sweary-words (some of them new :D) i simply <restored> the offending files from the waste-bin, then went to where they were, and killed them with <Shift><Delete> which by-passes the waste-bin. :)

I don't know if this will work for you, but it may well be worth a try...

---

### Post by sisco311 on 2008-11-10
> **c/Kr3t said:**
> Whenever I go to empty my trash bin, there is always files left in there.  No matter how many times I try to empty it they never go away.

I've tried going to the trash directory with sudo nautilus but that always says that it cannot access it, directory doesn't exist.

open a terminal and run:
```
sudo chown -R $USERNAME: ~/.local/share/Trash/
```then try to empty the trash.

---

### Post by c/Kr3t on 2008-11-10
success!!! both of them worked on separate files  thanks guys

---

### Post by sisco311 on 2008-11-10
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

### Post by aged hippy on 2008-11-10
Good one. :)

---

