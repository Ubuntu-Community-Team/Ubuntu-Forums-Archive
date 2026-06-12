---
title: "problems with root passwd"
date: 2005-07-05
forum: Desktop Environments
---

### Post by rpm on 2005-07-05
Hi all,

I'm able to work properly with kubuntu from the shell using the root password but when I try to use some graphical tools the root password doesn't work at all.

I post this topic due to a help request from a friend of mine, instead I use ubuntu hoary (not kde) without problems.

Can you suggest us which could be the problem.. ?

thx

---

### Post by codejunkie on 2005-07-05
run the app lets say kcontrol like so 
```

kdesu kcontrol

```
adding kdesu plus the name of the app opens it with root permissions hope this helps.

---

### Post by rpm on 2005-07-05
thx

---

### Post by Firetech on 2005-07-05
In Kubuntu, kdesu uses sudo, so the password it wants is really the user password (even if it says root password...)

---

