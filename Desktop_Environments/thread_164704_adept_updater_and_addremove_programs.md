---
title: "adept updater and add/remove programs"
date: 2006-04-23
forum: Desktop Environments
---

### Post by katana2k on 2006-04-23
since updating to Kubuntu 6.01 ive been getting the same error message when i try to open adept updater or the add/remove programs thing:

```
The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem.
```

Ive been doing everything by the terminal so far, including apt-get update and i thiss get this message. the command apt-setup doesnt exist either :/

any ideas?

---

### Post by faktorqm on 2006-05-01
hi, try this in a terminal:

sudo debtags update

bye!

---

### Post by vmifox on 2006-05-02
Thanks -  worked for me.  I installed 6.06 beta1, fresh, yesterday (from install CD ~ the livecd overwrite my partition table - problem is fixed in beta2).  I've been reading about ubuntu since it was first announced, but this is my first time to try it - so far pretty good, forums have been helpful.

---

