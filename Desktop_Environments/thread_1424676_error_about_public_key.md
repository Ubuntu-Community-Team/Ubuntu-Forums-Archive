---
title: "error about public key"
date: 2010-03-08
forum: Desktop Environments
---

### Post by tonjaa on 2010-03-08
9.10 64bit
i try to update but have error about GPG error it's tell public key not available .
how i fix this problem how to add public key ?

---

### Post by MelDJ on 2010-03-08
try the link in my sig

---

### Post by sisco311 on 2010-03-08
You have to add the repository's public key to the list of your trusted keys:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 219ec810
```

---

### Post by tonjaa on 2010-03-08
thank you so much that i have some error with program Tor it's use key and i remove program now it's ok.

---

