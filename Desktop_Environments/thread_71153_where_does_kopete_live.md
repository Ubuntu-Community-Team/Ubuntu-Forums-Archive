---
title: "where does kopete live?"
date: 2005-10-02
forum: Desktop Environments
---

### Post by Brando569 on 2005-10-02
im trying to install kopete 10.3 via svn but i dont know where it lives so i cant use the --prefix option with configure, which i need to. ive tried searching around but cant find it.

---

### Post by Freddy on 2005-10-02
You can use, 
```
./configure --prefix=`kde-config --prefix`
```
and make the kde-config direct where it wan't your kopete.   /// Freddan

---

