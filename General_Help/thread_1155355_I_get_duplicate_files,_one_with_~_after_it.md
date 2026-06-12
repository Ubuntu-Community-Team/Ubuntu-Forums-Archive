---
title: "I get duplicate files, one with ~ after it?"
date: 2009-05-10
forum: General Help
---

### Post by Beezleray on 2009-05-10
Whenever I create a file or edit something there always appears a duplicate file with a tilda after it and never goes away. What is this and how can I stop it?

---

### Post by Vaphell on 2009-05-10
it's a backup file made by gedit, can be useful when you mess with system configuration files :-)
my guess is you can turn it off in gedit preferences -> [v] create backups before saving (or something like that)

---

### Post by BslBryan on 2009-05-10
Hello, Beezleray. :-)

Vaphell is right.  If you want an application to find all of these double files, though, there is one in the repositories that's pretty simple.

```
sudo apt-get install fdupes
```

Best to you. :-)

---

