---
title: "[icewm] Start menu"
date: 2006-08-28
forum: Desktop Environments
---

### Post by ashrack on 2006-08-28
Is it possible to make the start menu open new subfolders only by moving the mouse on an item instead of having to click on them?

---

### Post by lagagnon on 2006-08-28
Yes. You need to edit the ~/.icewm/preferences file. There are about 200 different aspects you can change there. It should be quite  obvious once you read through them all - but I cannot exactly remember which one you have to change but I think it is:

MenuMouseTracking = 1

try it.

---

### Post by erwinquita on 2006-08-28
> **lagagnon said:**
> Yes. You need to edit the ~/.icewm/preferences file. There are about 200 different aspects you can change there. It should be quite  obvious once you read through them all - but I cannot exactly remember which one you have to change but I think it is:

MenuMouseTracking = 1

try it.

Yup this is the right way to do it. :) 
BTW
what version of icewm are you using?

---

### Post by ashrack on 2006-08-29
> **lagagnon said:**
> Yes. You need to edit the ~/.icewm/preferences file. There are about 200 different aspects you can change there. It should be quite  obvious once you read through them all - but I cannot exactly remember which one you have to change but I think it is:

MenuMouseTracking = 1

try it.

Tanx men! Been looking for it in ICEPREF but strangely I cant find it.
Now menumouse tracking works.

btw. How do I manually reset ICEWM when changing something in the preferences file so the changes takes effect

---

### Post by ashrack on 2006-08-29
> **erwinquita said:**
> Yup this is the right way to do it. :) 
BTW
what version of icewm are you using?
Im using 1.2.23-3ubuntu1. Which according to ICEWM site is a pretty old version! How come such an old version resides in DAPPER repos?

---

