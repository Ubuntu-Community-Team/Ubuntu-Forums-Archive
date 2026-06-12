---
title: "Cedega"
date: 2006-08-28
forum: Desktop Environments
---

### Post by ESPOiG on 2006-08-28
when i goto install Cedega5.1 i get the error Error: Dependency is not satisfiable: xlibs

i have tried -
sudo apt-get install xlibs - no such thing
sudo apt-get install xlibs-dev - this is allready installed

any help would be great

---

### Post by frodon on 2006-08-28
This should work :
[http://ubuntuforums.org/showpost.php?p=1151432&postcount=3](http://ubuntuforums.org/showpost.php?p=1151432&postcount=3)

---

### Post by ESPOiG on 2006-08-28
thx mate

---

### Post by visik7 on 2006-08-28
generally when you install a package from .deb and not from a repository you should resolve dependancies using
```
apt-get -f install
```

---

