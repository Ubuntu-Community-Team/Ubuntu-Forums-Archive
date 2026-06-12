---
title: "[SOLVED] how do i delete and rename files as root?"
date: 2008-12-23
forum: General Help
---

### Post by andrewwg94 on 2008-12-23
i want to delete: /etc/rc2.d/S19rc.local
i want to rename: /etc/rc2.d/S99rc.local to S19rc.local

S19rc.local is a file i made up and i want to delete it b/c it doesn't work.

---

### Post by binbash on 2008-12-23
sudo rm /etc/rc2.d/S19rc.local
sudo mv /etc/rc2.d/S99rc.local /etc/rc2.d/S19rc.local

---

### Post by Coder543 on 2008-12-23
from the terminal:
sudo rm /etc/rc2.d/S19rc.local
sudo mv /etc/rc2.d/S99rc.local /etc/rc2.d/S19rc.local

from the nautilus:
(use terminal)
sudo nautilus
(now nautilus)
navigate to /etc/rc2.d/ and do your stuff.


edit:binbash beat me to it...

---

### Post by Titan8990 on 2008-12-23
sudo rm /etc/rc2.d/S19rc.local

sudo mv /etc/rc2.d/S99rc.local /etc/rc2.d/S19rc.local


> sudo nautilus

This should be:

gksu nautilus


but they both work

---

### Post by iponeverything on 2008-12-23
open a terminal and do:

```
gksu nautilus
```

---

### Post by andrewwg94 on 2008-12-23
what's the diffrence between gsuk or whatever and sudo?

---

### Post by Titan8990 on 2008-12-23
gksu should be used when launching **graphical** programs as root.

---

