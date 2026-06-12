---
title: "Terminal Command for starting/stopping Compiz Fusion"
date: 2010-02-13
forum: Desktop Environments
---

### Post by Burky on 2010-02-13
Is there a terminal command for starting/stopping Compiz Fusion?

---

### Post by oldos2er on 2010-02-13
```
compiz --replace
```
When you want metacity back, ```
metacity --replace
```

---

### Post by falconindy on 2010-02-13
You should append an '&' to the commands and then 'disown', or else you'll run into problems when you try and close the terminal window.

---

