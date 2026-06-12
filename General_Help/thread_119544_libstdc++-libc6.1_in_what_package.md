---
title: "libstdc++-libc6.1 in what package?"
date: 2006-01-19
forum: General Help
---

### Post by dguido on 2006-01-19
I was trying to install the V-ONE Smart Pass VPN Client and encountered this error after I tried running it: ```
./smartpass: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
```
Where can I get the library it's asking for?

---

### Post by kaamos on 2006-01-19
```
sudo apt-get install libstdc++5 libstdc++6
```

---

### Post by dguido on 2006-01-20
[QUOTE=kaamos]```
sudo apt-get install libstdc++5 libstdc++6
```[/QUOTE]
both are already the newest version :(
any others you know of?

---

