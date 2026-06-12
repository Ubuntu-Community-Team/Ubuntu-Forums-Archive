---
title: "geany"
date: 2009-01-16
forum: General Help
---

### Post by sridarshan on 2009-01-16
i have installed geany in  my ubuntu,but every time i compile it ,i get the following error message
compilation failed
/bin/sh:G++:not found

---

### Post by blazemore on 2009-01-16
Have you install the files required for build?
```
sudo apt-get install build-essential
```

---

### Post by adamlau on 2009-01-16
Or simply install g++.

---

### Post by jespdj on 2009-01-16
> **adamlau said:**
> Or simply install g++.
No, install build-essential, otherwise you still won't be able to compile programs without getting error messages. The package g++ just installs the bare compiler, and build-essential installs the compiler plus headers and library files that you need to compile programs.

---

