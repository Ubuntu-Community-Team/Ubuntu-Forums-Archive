---
title: "Any sound"
date: 2007-12-25
forum: Desktop Environments
---

### Post by Fegna on 2007-12-25
I can't get any sound in my Toshiba laptop

---

### Post by TidusBlade on 2007-12-25
Any other info? 
Anyways, what distro are you running and whats your sound card? You can find all that by using the command "hardinfo" and first installing it using "sudo apt-get install hardinfo".

---

### Post by eggdeng on 2007-12-25
```
aplay -l
``` (lowercase L, not 1)
will identify your sound card.

---

