---
title: "quick way of disabling and re-enabling compiz?"
date: 2009-06-16
forum: Desktop Environments
---

### Post by pjo123 on 2009-06-16
Wine advises me not to have compiz enabled when I run it.

I like compiz being enabled (I have compizconfig settings manager installed)

Is there a simple/quick way I can disable it before running wine and enable it after running wine please?

thanks

---

### Post by Aearenda on 2009-06-16
Looks like it can be done by ```
metacity --replace &
```to turn compiz off, and ```
compiz --replace &
```to turn it on. The '&' markers cause a new process to be created, so that the existing process can go on to the next command (try it without the '&' in a terminal to see what I mean).

---

### Post by iamnotthemessiah on 2009-06-16
fusion-icon

---

### Post by pjo123 on 2009-06-16
many thanks

---

