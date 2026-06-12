---
title: "remove cedega"
date: 2006-09-08
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-08
Itried sudo apt-get remove cedega and it said no package installed but it is and listed in Applications-TransGaming. I have had nothing but trauma with wine & cedega. Trying to use Game House games. Any thoughts??

---

### Post by Mithrilhall on 2006-09-08
I don't think you can 'apt-get remove cedega' if you didn't apt-get install it...but then again I could be wrong.

---

### Post by divague on 2006-09-08
how did you installed cedega, from a .deb file? o from a tar.gz or tar.bz2 file?

---

### Post by Virgilius on 2007-06-02
Well, I'm having the same problem here and I used .deb for my install of Cedega

---

### Post by taurus on 2007-06-02
> **Virgilius said:**
> Well, I'm having the same problem here and I used .deb for my install of Cedega

Try to remove it from a terminal like

Applications -> Accessories -> Terminal
```
sudo dpkg -r cedega
```

---

