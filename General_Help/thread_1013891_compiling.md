---
title: "compiling"
date: 2008-12-17
forum: General Help
---

### Post by zero_ZX on 2008-12-17
Hi all, i tried to compile (after a readme)
and i got following error:
g++ -Wall -O3 -I ../ -Wno-multichar -fPIC -c bsha1.cpp -o bsha1.o
make: g++: Command not found
make: *** [bsha1.o] Error 127

Any one has any idea on what that means? - and how to solve it? :)

---

### Post by SuperSonic4 on 2008-12-17
Have you installed build-essential, I'm pretty certain that g++ is in that package ```
sudo apt-get install build-essential
```

---

### Post by zero_ZX on 2008-12-17
thanks! worked great

---

