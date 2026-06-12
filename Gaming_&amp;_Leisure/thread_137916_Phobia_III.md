---
title: "Phobia III"
date: 2006-02-28
forum: Gaming &amp; Leisure
---

### Post by krye on 2006-02-28
I can't seem to get this one running, anyone has tried it?

For the two first libraries it asked me for some symlinks solved the problem, but now it's asking me for libstdc++-libc6.2-2.so.3, and I can't find it on my system nor in any package:

```
./phobia3: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
```

The game's page is [http://www.redlynx.com/phobiaIII/](http://www.redlynx.com/phobiaIII/) if anyone wants to try it out.

Any help is deeply apprecciated :)

---

### Post by calgarystevens on 2006-03-01
Using apt-file I discovered this package: libstdc++2.10-glibc2.2 and possibly this also: libstdc++2.10-dbg Try searching for them in Synaptic and you might have your game working. If it works, that'll be amazing, you'll be the first person I've helped (besides myself of course) :-)

---

### Post by krye on 2006-03-02
It worked :D

Thank you!!!

---

