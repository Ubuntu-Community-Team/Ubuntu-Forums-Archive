---
title: "Cannot edit sources.list"
date: 2009-03-07
forum: General Help
---

### Post by ranger_cole on 2009-03-07
when I issue the command:
sudo vi /etc/apt/sources.list

I get a message:
E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
I have 3 sources files:
sources.list, sources/list.save, and sources.list.20090301125833
I cannot add remastersys to the sources.

---

### Post by benblout on 2009-03-07
What happens if you issue the commmands
```
sudo ls -al sour*
sudo ls -al .sour*
```

---

