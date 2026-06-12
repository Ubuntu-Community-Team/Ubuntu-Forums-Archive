---
title: "UT2004 Server - Shared Library Error"
date: 2008-09-16
forum: Gaming &amp; Leisure
---

### Post by Evil_Network on 2008-09-16
I'm having some trouble getting a UT server running on Hardy Heron (8.04). When I attempt to start the server I am presented with this error...

***error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory***

I'm not having much luck on a forum search. Hoping someone can shed some light on the subject.

BTW - the 3355 and 3369 patches were installed.

TIA - Peace.

--Evil

---

### Post by Perfect Storm on 2008-09-16
```
sudo apt-get install libstdc++5
```

---

### Post by Evil_Network on 2008-09-16
I'm obviously an idiot...

Thanks. Library installed, problem solved.

---

