---
title: "Freeze application on purpose (?)"
date: 2009-04-10
forum: Desktop Environments
---

### Post by Keio on 2009-04-10
Hello,
Do you know when an application says "Not Responding"? Well.. I need to do it on purpose.

So, do you know any way that could let me freeze any (or a specific one) application whenever I need it to and then unfreeze it again when I want?

Thank you :)

---

### Post by Peasantoid on 2009-04-10
```
kill -STOP <pid>
or:
killall -STOP <name>
```
Replace -STOP with -CONT to unfreeze.

---

### Post by Keio on 2009-04-10
Thank you very much for your answer. Very usefull. :)

---

### Post by Keio on 2009-04-10
Sorry, I actually need to stop a flash application inside firefox (or any browser) is there a pid for the flash plugin?

If a freeze firefox, well.. it only freezes firefox, not the plugins.

EDIT: If you want to freeze the flash plugin freeze npviewver.bin

---

