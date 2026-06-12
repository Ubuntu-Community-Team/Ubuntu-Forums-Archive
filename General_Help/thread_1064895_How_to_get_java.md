---
title: "How to get java"
date: 2009-02-09
forum: General Help
---

### Post by rlaknar on 2009-02-09
Hi.Anyone please tell me how to get java jdk latest version for Ubuntu 8.10.I dont like to work with IDE.I need all the java packages only.Please tell me where to get.If it is full package of one download, it would be better because I have to install the same package for the computer having no internet facility.

---

### Post by lykwydchykyn on 2009-02-09
The package you need from the repositories is sun-java6-jdk.  If you're installing offline, you'll need that package plus sun-java6-bin.

You can get them from here:
[http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/s/sun-java6/)

---

### Post by Fixman on 2009-02-09
> **rlaknar said:**
> Hi.Anyone please tell me how to get java jdk latest version for Ubuntu 8.10.I dont like to work with IDE.I need all the java packages only.Please tell me where to get.If it is full package of one download, it would be better because I have to install the same package for the computer having no internet facility.

```
 sudo apt-get install -d sun-java6-bin 
```

All packages will be in /var/cache/apt/archives.

---

### Post by rlaknar on 2009-02-09
> **Fixman said:**
> ```
 sudo apt-get install -d sun-java6-bin 
```

All packages will be in /var/cache/apt/archives.



Thank you very much.

---

