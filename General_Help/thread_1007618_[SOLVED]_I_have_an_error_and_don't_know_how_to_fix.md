---
title: "[SOLVED] I have an error and don't know how to fix it."
date: 2008-12-10
forum: General Help
---

### Post by Freddie1984 on 2008-12-10
the error I have is E: dpkg was interrupted,you must manually run 'dpkg --configure -a' to correct the problem.E:_cache->open()failed,please report. I have no clue what this error is about I was trying to install limewire and it didn't finish it stopped on sunjava If anyone can help I would appreciate it thanks

---

### Post by adult swim on 2008-12-10
go to a terminal applications>accessories>terminal
then enter in ```
sudo dpkg --configure -a
```
it will ask for your password, type that in and hit enter
then enter in ```
sudo apt-get update
```
that should fix your problem

---

