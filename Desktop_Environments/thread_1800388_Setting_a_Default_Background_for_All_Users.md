---
title: "Setting a Default Background for All Users"
date: 2011-07-08
forum: Desktop Environments
---

### Post by csplu on 2011-07-08
Sorry if this question has been asked before, but I am trying to figure out how to set a custom default background so that any user that logs onto the machine (via our LDAP server) will see the background that I have set to be default.  

I am extremely new to Ubuntu (mainly a Windows person) but am trying to create this environment to give our students an option to boot either into Windows or Ubuntu.

If anyone could give me some help or point me in the right direction, I would greatly appreciate it.

---

### Post by wojox on 2011-07-08
Check out:

```
/var/lib/gconf/debian.defaults/%gconf-tree.xml
```

---

