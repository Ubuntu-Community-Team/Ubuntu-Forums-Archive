---
title: "Eschalon Book I demo install help"
date: 2008-07-01
forum: Gaming &amp; Leisure
---

### Post by anotherconfused1 on 2008-07-01
I can't get Eschalob Book I running. 
justin@justin-desktop:~$ cd Desktop/eschalon_book_1_demo
justin@justin-desktop:~/Desktop/eschalon_book_1_demo$ ./eschalon_book_1_demo
./eschalon_book_1_demo: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
justin@justin-desktop:~/Desktop/eschalon_book_1_demo$ 
What happened to libstdc++.so.5?

---

### Post by Cappy on 2008-07-01
For 32-bit Ubuntu:
```
sudo apt-get install libstdc++5
```

For 64-bit Ubuntu:
```
sudo apt-get install ia32-libs
```

You can use Synaptic to install the package too.

---

### Post by anotherconfused1 on 2008-07-01
Thanks it worked!

---

