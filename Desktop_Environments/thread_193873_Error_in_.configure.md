---
title: "Error in ./configure"
date: 2006-06-10
forum: Desktop Environments
---

### Post by RotoGrip on 2006-06-10
Hi all,

 Im trying to install K9copy. and end up with this error.

"configure: error: no acceptable C compiler found in $PATH"
 
I looked into Synaptic for C compiler but didnt find anything. How can i solve this issue?

---

### Post by arnieboy on 2006-06-10
[QUOTE=RotoGrip]Hi all,

 Im trying to install K9copy. and end up with this error.

"configure: error: no acceptable C compiler found in $PATH"
 
I looked into Synaptic for C compiler but didnt find anything. How can i solve this issue?[/QUOTE]
```
sudo apt-get install gcc g++ make build-essential
```

---

### Post by kaamos on 2006-06-10
install the package "build-essential".

---

