---
title: "apt-bouild build also dependancies"
date: 2009-04-08
forum: General Help
---

### Post by pacman401 on 2009-04-08
Hello

How to do that apb-build also dependancies

for example sudo apt-build install firefox 
apb-build is building firefox but dependancies packages are normally downloading and istalling like a xulrunner

but i wanna to looks like that

sudo apt-build install firefox 
apb-build is building firefox and xulrunner

(yeah i know i can sudo apt-cache show PKG_NAME and dependancies but I want to apt-build do it automaticly)

how to do that ?

---

### Post by MaindotC on 2009-04-08
If you want to install the dependency libraries for a package, but not the package itself, the command is:
```

sudo apt-get build-dep <package_name>

```

---

