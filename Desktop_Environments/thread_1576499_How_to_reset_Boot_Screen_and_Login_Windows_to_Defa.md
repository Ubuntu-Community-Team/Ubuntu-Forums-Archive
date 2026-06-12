---
title: "How to reset Boot Screen and Login Windows to Default"
date: 2010-09-17
forum: Desktop Environments
---

### Post by rudysuryanto on 2010-09-17
I want to reset Boot Screen and Login Window to Default. How to do it? Thank's.

---

### Post by gjonatha on 2010-09-17
You can use the startupmanager

sudo apt-get install startupmanager

Then go to System > Administration > Start up Manager and configure your default os to boot up with.

---

### Post by luvshines on 2010-09-17
You may try
```
update-alternatives --config default.plymouth
```

If you have many boot screens, you should get a list of all.
'*' symbol in the left shows which one is active

You can choose the first one,[auto] by selecting 0 and that should fix it

---

