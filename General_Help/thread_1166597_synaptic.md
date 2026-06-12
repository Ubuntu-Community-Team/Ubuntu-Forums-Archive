---
title: "synaptic"
date: 2009-05-21
forum: General Help
---

### Post by cowboy7305 on 2009-05-21
when i open thhe synaptic i get this error message
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.
when i run this in terrminal i get i need to be a super user
dpkg --configure -a
i have no idea what is wrong
using 8.10

---

### Post by sgosnell on 2009-05-21
sudo gives you temporary superuser powers.  

sudo dkpg --configure -a

---

### Post by dhughes on 2009-05-21
I concur.

---

### Post by cowboy7305 on 2009-05-21
have done that i get this message 
sudo: dkpg: command not found

---

### Post by Yellow Pasque on 2009-05-21
There was a typo.
Post output of this (if it ends in an error):
```
sudo dpkg --configure -a
```

---

### Post by cowboy7305 on 2009-05-21
Setting up java-common (0.30ubuntu3) ...

Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeepe

---

### Post by sgosnell on 2009-05-21
Looks like it worked.  Those aren't errors.

---

### Post by cowboy7305 on 2009-05-21
many thanks

---

### Post by sgosnell on 2009-05-21
Por nada.  You'll need to remember sudo, because it's required to allow any changes to any system files other than your user files.  You'll get used to it.

---

