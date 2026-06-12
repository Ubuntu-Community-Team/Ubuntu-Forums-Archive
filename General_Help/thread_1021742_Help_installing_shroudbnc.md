---
title: "Help installing shroudbnc"
date: 2008-12-25
forum: General Help
---

### Post by Coffey522 on 2008-12-25
Ok I'm trying to install shroudbnc, I typed wget [http://slygaming.com/archives/sbnc/sbnc-1.2.tar.gz](http://slygaming.com/archives/sbnc/sbnc-1.2.tar.gz) and that worked fine. Then I typed tar -zxf sbnc-1.2.tar.gz and that worked too, but when I type cd sbnc-1.2.tar.gz it says bash: cd: sbnc-1.2.tar.gz: Not a directory 

what does that mean and how can I fix that error? :confused:

---

### Post by Coffey522 on 2008-12-26
help

---

### Post by cariboo on 2008-12-26
Have you tried:

```
cd sbnc-1.2
```

Make sure you have build-essential installed and read all the readme and install files.

Jim

---

### Post by Ahadiel on 2008-12-26
> **Coffey522 said:**
> Ok I'm trying to install shroudbnc, I typed wget [http://slygaming.com/archives/sbnc/sbnc-1.2.tar.gz](http://slygaming.com/archives/sbnc/sbnc-1.2.tar.gz) and that worked fine. Then I typed tar -zxf sbnc-1.2.tar.gz and that worked too, but when I type cd sbnc-1.2.tar.gz it says bash: cd: sbnc-1.2.tar.gz: Not a directory 

what does that mean and how can I fix that error? :confused:

The archive may have extracted itself into the current directory (meaning it's not in another folder).

---

