---
title: "Can not see boot screen"
date: 2008-12-17
forum: General Help
---

### Post by iDellG3 on 2008-12-17
Hello Ununtu forums, I have installed a new crt monitor on my computer, and each time I boot onto Ubuntu, I can not see the loading screen, and I was wondering if there is any way I can change the screen resolution of the boot screen so I can see it? it looks like the boot screen is running at a different resolution from the last monitor and this one does not recognise it.

---

### Post by theozzlives on 2008-12-17
yes:
```
sudo apt-get install startup-manager
```
it'll go in system>>administration

---

### Post by iDellG3 on 2008-12-17
it did not work, it says "E: could not find package starup manager"

---

### Post by taurus on 2008-12-17
Shouldn't it be startupmanager?

```
sudo apt-get update
sudo apt-get install startupmanager
```

---

