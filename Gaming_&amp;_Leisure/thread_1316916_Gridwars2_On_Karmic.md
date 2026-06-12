---
title: "Gridwars2 On Karmic"
date: 2009-11-06
forum: Gaming &amp; Leisure
---

### Post by dragonboss on 2009-11-06
Can't install gridwars2 on ubuntu 9.10 it says unsatisfiable dependencies from the deb file and the zip file executes for 2 seconds and closes

---

### Post by canseco on 2009-11-06
You need to install libstdc++5 from here [http://packages.debian.org/lenny/libstdc++5](http://packages.debian.org/lenny/libstdc++5)

---

### Post by dragonboss on 2009-11-07
Ok, Great! It works! Now how do you get the music playing in the game cos the file i have has game music but it does not seem to play.

---

### Post by coolen on 2009-11-20
I installed that package, but it still won't run (complaining that it's missing :S)

```
****@********:~$ /usr/games/gridwars
./gridwars: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

****@********:~$ ls -l /usr/lib/libstdc++.so.5
lrwxrwxrwx 1 root root 18 2009-11-18 19:37 /usr/lib/libstdc++.so.5 -> libstdc++.so.5.0.7
```

Seems it's all there...unless gridwars expects the library elsewhere?

---

