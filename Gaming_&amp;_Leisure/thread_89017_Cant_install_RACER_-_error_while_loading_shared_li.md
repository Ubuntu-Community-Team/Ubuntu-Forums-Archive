---
title: "Cant install RACER - error while loading shared libraries: libstdc++.so.5"
date: 2005-11-11
forum: Gaming &amp; Leisure
---

### Post by jkb on 2005-11-11
I'm trying to install and run Racer 0.5.2.
Installed "racer_0.5.2beta8.9-english.run"

Under the installation I get lots of warnings and when I try starting the game it won't run.
I get this error:
"Error loading new keyboard description
./racer.bin: error while loading shared libraries: libstdc++.so.5: cannot open s hared object file: No such file or directory"

What to do? please help!!

/JKB

---

### Post by Perfect Storm on 2005-11-12
It says you don't have libstdc++5 installed.

```

sudo apt-get install libstdc++5

```

---

