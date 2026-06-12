---
title: "open a new terminal from a terminal"
date: 2009-02-04
forum: General Help
---

### Post by Ristar on 2009-02-04
hello, i need to write a bash script to open a new terminal and have that new terminal run another bash script to run a program.

please help. thanks.

---

### Post by jpeddicord on 2009-02-04
Moved to General Help - Tutorials & Tips is *not* a support forum.

---

### Post by mb_webguy on 2009-02-05
```
gnome-terminal -x *script*
```

This assumes that the script is located in the user's path, such as in ~/bin (if only a specific user needs to access the script) or /usr/local/bin (to make it available to all users).

---

