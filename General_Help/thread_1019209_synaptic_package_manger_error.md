---
title: "synaptic package manger error"
date: 2008-12-22
forum: General Help
---

### Post by rem- on 2008-12-22
When I run the Synaptic package manager I get this error
on startup. This was after an install hung up in terminal window and I X'd out:
____________________
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
_____________________________________
when run 'dpkg --configure -a' in terminal this is output
_________________________
rem@ubuntu:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
rem@ubuntu:~$ 
____________________________
thanks [http://identi.ca/rem](http://identi.ca/rem)

---

### Post by taurus on 2008-12-22
```
sudo dpkg --configure -a
sudo apt-get update
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by rem- on 2008-12-23
My many thanks worked like a charm and I learned who superuser is..merry christmas

[http://rem091.wordpress.com](http://rem091.wordpress.com)
[http://identi.ca/rem](http://identi.ca/rem)

---

