---
title: "The dependency problems are back with Racer!"
date: 2006-07-14
forum: Gaming &amp; Leisure
---

### Post by RJARRRPCGP on 2006-07-14
I had Racer playable, but any track that I tried other than the track that came with Racer had video corruption and I had errors in the Racer log file, QLOG, thus I suspect a broken Racer release. I downgraded from 0.5.2 beta 8.9 to 0.50. After I did I'm getting the following error message, even when libstdc++ is installed:

```

./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory 
```

Still no change even after I reinstalled it with Synaptic.:evil: ](*,)

---

### Post by vem0m on 2006-07-14
try doing the following from terminal
```
sudo apt-get install libstdc++6 libstdc++6-dev
```

and see if that works let us know :)

---

### Post by RJARRRPCGP on 2006-07-16
The filename version is misleading. I solved the problem already.:confused:

---

