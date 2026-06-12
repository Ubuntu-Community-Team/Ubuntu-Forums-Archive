---
title: "help uninstalling a program"
date: 2006-09-11
forum: Desktop Environments
---

### Post by lonelypauly on 2006-09-11
i need to uninstall azureus but for some reason it isn't listed as being installed...however, azureus is my default bt client and runs every time i dl a torrent...so it must be installed somewhere, right?

i forgot how or what i used to install azureus but its in the repos as not being installed and shows that it isn't installed in the add/remove manager either.

any ideas?

---

### Post by lwr on 2006-09-11
try doing ```
sudo aptitude remove azureus
```

---

### Post by nikhilk on 2006-09-11
One of the causes of the problem you are facing can be due to installing from source using "make" and "make intall". Can you somehow confirm that?

---

