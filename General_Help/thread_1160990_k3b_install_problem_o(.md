---
title: "k3b install problem :o("
date: 2009-05-16
forum: General Help
---

### Post by aluget on 2009-05-16
I have tried to run k3b after an upgrade to Jaunty and get an error message when trying to run k3b from the terminal
k3b: error while loading shared libraries: libdbus-qt-1.so.1: cannot open shared object file: No such file or directory

I've tried removing k3b and reinstalling it but the problem remains
Any Ideas??

---

### Post by jpeddicord on 2009-05-16
Moved to General Help; Tutorials & Tips is not a support forum. :)

---

### Post by x33a on 2009-05-16
try 

```
sudo aptitude purge k3b
```

then 

```
sudo aptitude update && sudo aptitude install k3b
```

---

### Post by aluget on 2009-05-16
Thanks heaps x33a. I tried something similar earlier but with no luck. Its up and running beautifully now :o)

---

