---
title: "Synaptic Package Manager Help"
date: 2009-03-17
forum: General Help
---

### Post by sargeant dread on 2009-03-17
I tried to use the synaptic manager to install the kubuntu desktop but unfortunately i got this
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
What can i do to get the package manager to work properly again?

---

### Post by taurus on 2009-03-17
Close synaptic.  Then open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by sargeant dread on 2009-03-17
o i forgot to type sudo, duh

---

