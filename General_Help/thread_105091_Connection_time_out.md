---
title: "Connection time out"
date: 2005-12-17
forum: General Help
---

### Post by softwarepirate on 2005-12-17
Every time i try to get crystal space from the package managers it wont download all the way it keeps timing out is there any thing i can do about this?

---

### Post by NotJustANewbie on 2005-12-17
Change your repositories.
```
sudo gedit /etc/apt/sources.list
```

And where-ever it says your country's letters (e.g. "gb" for great britain), change it to "de" or "gb" and then:
```
sudo apt-get update
```

and try downloading again.

---

