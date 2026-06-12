---
title: "&quot;dpkg was interrupted&quot;"
date: 2008-12-19
forum: General Help
---

### Post by Warriorccc0 on 2008-12-19
Now whenever I use the Add/Remove Applications and try to add something new I get this:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

and when I try and do that I get this:

```
requested operation requires superuser privilege

```


How would I go about fixing this problem?

---

### Post by cdtech on 2008-12-19
Copy and paste this command into a terminal:
```
sudo dpkg --configure -a && sudo apt-get -f install
```
This will configure all of the packages that where interrupted.

---

### Post by Warriorccc0 on 2008-12-19
Ah, thank you.

---

### Post by jmszr on 2008-12-19
WarriorcccO,
             Run: sudo dpkg --configure -a

---

### Post by hyper_ch on 2008-12-20
reading the error messages often helps :)

---

