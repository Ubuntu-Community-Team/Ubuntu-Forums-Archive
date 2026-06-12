---
title: "Got an error message"
date: 2008-04-13
forum: Dell  Ubuntu Support
---

### Post by ozweego5 on 2008-04-13
I get this error message when i start my synaptic package manager 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
 
any one got  any suggestions???? 
Thanks

---

### Post by Chilongola on 2008-04-13
I believe you fix this right from the menu....

---

### Post by Michael.Godawski on 2008-04-14
Try to run this in terminal

```
sudo dkpg --configure -a
```

---

### Post by ozweego5 on 2008-04-14
yeah i tried sudo dkpg --configure -a and it just says command not found??

---

### Post by kellemes on 2008-04-14
> **ozweego5 said:**
> yeah i tried sudo dkpg --configure -a and it just says command not found??

It is ```
sudo dpkg --configure -a
```

---

### Post by ozweego5 on 2008-04-14
Thanks a bit, that did the trick! I  love UBUNTU Support!!

---

