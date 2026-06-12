---
title: "Terminal Problem With apt-get"
date: 2005-10-24
forum: Desktop Environments
---

### Post by rsulli55 on 2005-10-24
When I am in the terminal and try to apt-get something it always says there is no such file. For example:
```
ryan@ubuntu:~$ sudo apt-get install gdesklets
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package gdesklets

```

Am I doing something wrong?  Does anyone know how to fix this?

---

### Post by Xian on 2005-10-24
[QUOTE=rsulli55]Am I doing something wrong?  Does anyone know how to fix this?[/QUOTE]
Just add the [Extra Software Repositories](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse).

```
~$ apt-cache policy gdesklets
gdesklets:
  Installed: 0.35.2-1build1
  Candidate: 0.35.2-1build1
  Version table:
 *** 0.35.2-1build1 0
        500 http://us.archive.ubuntu.com breezy/universe Packages
        100 /var/lib/dpkg/status
```

---

