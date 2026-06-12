---
title: "adept  manager problem"
date: 2007-04-07
forum: Desktop Environments
---

### Post by cosmo18 on 2007-04-07
whenever I try to run the adept package manager it gives me an error message that says "Another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one"
I have not started any other package managers and I even tried 
```
sudo rm /var/lib/dpkg/lock
```
 how do I find what other program is running and shut it down?

---

### Post by cosmo18 on 2007-04-07
I seemed to have fixed it by running ```
sudo apt-get clean && sudo apt-get update
```

---

