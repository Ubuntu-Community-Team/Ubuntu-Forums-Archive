---
title: "fubar'd my /home dir --help?"
date: 2009-01-18
forum: General Help
---

### Post by deth_X_Cycle on 2009-01-18
I mistakenly changed my /home folder to an external hard drive using GUI Admin- System- Groups and users, etc. Now when I boot up I get the following error:
"Your home directory is listed as: '/media/WorkforMe/Home/james' but it does not appear to exist.  Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session."  many error messages follow.  I can get in to the failsafe terminal... What is the best way to change back to my original /home directory?

---

### Post by heindsight on 2009-01-18
boot into recovery mode and do:
```
usermod -d /home/username username
```

---

### Post by deth_X_Cycle on 2009-01-18
Thanks that helped immensely... and was surprisingly easy.

---

