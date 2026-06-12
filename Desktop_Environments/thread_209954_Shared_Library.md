---
title: "Shared Library"
date: 2006-07-05
forum: Desktop Environments
---

### Post by majkmil on 2006-07-05
Hi, I am trying to install RealPlayer on my ppc IBook. When I try to install RP it says I need  libstdc++.so.5. I downloaded the file and have it on my Desktop. Can I just put in the right directory and where does it go? I have been trying this for some time and I think I am getting close.  Help Please.

---

### Post by evilghost on 2006-07-05
In terminal, type:

```

sudo apt-get install libstdc++5

```

---

### Post by taurus on 2006-07-05
You need to put it in either /lib or /usr/lib...

---

### Post by adwait on 2006-07-05
Better if you install it using aptitude
```
sudo apt-get install libstdc++5
```

---

### Post by majkmil on 2006-07-05
Thanks guys, It seems to be installing but very slow. I will keep you posted.

---

