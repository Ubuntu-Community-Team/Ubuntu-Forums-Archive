---
title: "Shutdown, restart, log out icon"
date: 2011-06-03
forum: Desktop Environments
---

### Post by Borrot on 2011-06-03
Hi!

I'm wondering if it's possible to create a desktop icon that(when you click on it) gives you the alternatives "Shutdown, restart or log out" on ubuntu.

Is there any way to accomplish this?

Thanks in advance!

---

### Post by vangelas on 2011-09-15
I think you can do it through "screenlets". You can install through the repositories and then select the shutdown screenlet.

---

### Post by Frogs Hair on 2011-09-15
Vangelas is correct and if you want the most up to date stable version for 11.04 add this PPA via the terminal .

```
sudo add-apt-repository ppa:screenlets/ppa
``` 
```
sudo apt-get update
```
```
sudo apt-get install screenlets
```

---

