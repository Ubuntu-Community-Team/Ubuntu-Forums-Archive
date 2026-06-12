---
title: "virtualbox not recognizing vdi"
date: 2009-05-27
forum: General Help
---

### Post by zero777zero on 2009-05-27
where am i going wrong here? i made this .vdi on a previous ubuntu installation and figured that i would simply be able to copy the .vdi and use it with my new ubuntu installation

[http://img172.imageshack.us/img172/1339/screenshotwzg.png](http://img172.imageshack.us/img172/1339/screenshotwzg.png)

---

### Post by albinootje on 2009-05-27
> **zero777zero said:**
> i made this .vdi on a previous ubuntu installation and figured that i would simply be able to copy the .vdi and use it with my new ubuntu installation


That should usually work indeed. What is the error that you're getting ?

---

### Post by zero777zero on 2009-05-27
not showing up ?_?

[http://img245.imageshack.us/img245/322/screenshotiur.png](http://img245.imageshack.us/img245/322/screenshotiur.png)

---

### Post by albinootje on 2009-05-27
> **zero777zero said:**
> not showing up ?_?


Ah, I see... but if you wanted to have the whole setup that you had before, you should have copied the whole .VirtualBox/ directory from your old installation.

If it is too late for that, you can still create a new guest VM section, and then choose the vdi you have as "existing hard disk".

---

