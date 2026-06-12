---
title: "The output of ls is not color coded"
date: 2011-12-31
forum: Desktop Environments
---

### Post by adit on 2011-12-31
The output of ls is not color coded.
This problem started after I deleted all hidden files (files that start with a dot) in my home directory.

---

### Post by Lampi on 2011-12-31
I think you miss .bashrc, but to be save: copy all of them from /etc/skel to your home directory, then log out and back in again.

---

### Post by nothingspecial on 2011-12-31
```
cp /etc/skel/{.bashrc,.bash_logout,.profile} ~/ && . ~/.bashrc
```
 should sort you out.

---

### Post by adit on 2011-12-31
```
cp /etc/skel/{.bashrc,.bash_logout,.profile} ~/ && . ~/.bashrc
```
The above code worked (even without logging out).  Thank you.

---

### Post by kf5jak on 2013-02-22
I know this thread is old, however it did help solve the same problem I had.  I'd like to know why that worked though, if someone wouldn't mind explaining.

---

