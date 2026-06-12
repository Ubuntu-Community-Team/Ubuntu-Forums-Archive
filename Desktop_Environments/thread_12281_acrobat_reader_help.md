---
title: "acrobat reader help"
date: 2005-01-23
forum: Desktop Environments
---

### Post by danip on 2005-01-23
im trying to install the acro read plugin.  I do sudo apt-get install acroread-plugin and i get a bunch of errors 

```
W: Couldn't stat source package list http://archive.ubuntu.com warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com warty/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_warty_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
```

---

### Post by DJ_Max on 2005-01-23
run
```
sudo apt-get update
```

---

### Post by danip on 2005-01-23
yeah i do that but i still get errors

---

### Post by danip on 2005-01-23
Could i possibly have some of the source entires entered wrong?  Is there a place that has all of them listed so i can check that out?

---

### Post by DJ_Max on 2005-01-23
[QUOTE=danip]Could i possibly have some of the source entires entered wrong?  Is there a place that has all of them listed so i can check that out?[/QUOTE]
 That may be the problem.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by danip on 2005-01-24
thanks

---

