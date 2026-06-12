---
title: "My firefox doesnt startup"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Umbra on 2006-01-25
I installed firefox 1.5 using Automix, everything went ok but when i click on the icon the app appears in the task bar with a clock (initializing) and after some seconds desappears and nothing happens, how could i fix this?

---

### Post by earobinson on 2006-01-25
try runing it from the terminal post the error

---

### Post by Umbra on 2006-01-26
> /opt/firefox/firefox-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory  That one, anyway to fix?

---

### Post by aysiu on 2006-01-26
Did you try this? ```
sudo apt-get update
sudo apt-get install libstdc++5
```

---

