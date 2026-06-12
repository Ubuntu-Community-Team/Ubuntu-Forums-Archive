---
title: "update my videocard driver HELP!"
date: 2018-07-17
forum: Debian
---

### Post by darthgollo on 2018-07-17
hey! community I just install debian 9.05 in my computer I was wondering if I can update my videocard drivers 
the model is graphics 1024x768 the X.org fundation. 
the deal is I dont knoe how to, does someone can help me, thank you for your time :KS

---

### Post by deadflowr on 2018-07-17
*Thread moved to **Debian***

Open up a Terminal and post back the output form the following command
```
lspci | grep VGA
```

EDIT: my bad, I originally posted vga, the output is for a capitalized VGA.
fixed that.

---

