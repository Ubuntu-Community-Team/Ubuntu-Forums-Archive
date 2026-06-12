---
title: "Install Webmin"
date: 2008-12-03
forum: General Help
---

### Post by Eviltechie on 2008-12-03
Does anyone know how to install webmin? sudo apt-get install webmin dosen't seem to work. Same with apache, but I don't really need that. Are these packages server edition only?

This is the error I got.

```
ivan@ivan-ubuntu:~$ sudo apt-get install webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate
```

---

### Post by cybiko123 on 2008-12-03
> **Eviltechie said:**
> Does anyone know how to install webmin? sudo apt-get install webmin dosen't seem to work. Same with apache, but I don't really need that. Are these packages server edition only?

This is the error I got.

```
ivan@ivan-ubuntu:~$ sudo apt-get install webmin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate
```

Webmin isn't in the repos. You need to go to webmin.com and install it manually.

---

