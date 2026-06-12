---
title: "Root user question- Please Help!"
date: 2006-08-01
forum: Desktop Environments
---

### Post by mysticrider92 on 2006-08-01
I am kind of new to Ubuntu and I have been trying to install some packages that don't have instructions. One of them I tried to get by writing in the
web address ([http://winecvs.linux-gamers.net](http://winecvs.linux-gamers.net)) in the Repositories in Synapac. This added a line in the sources.list file (/etc/apt/sources.list), but now it tries to use that as the repository to look for everything. The problem is I can't delete the line in the sources.list file because I can't figure out how to access the file as root. I have tryed sudo, root terminal, and directly editing the file and it won't let me. It doesn't show up in the software properties, either.:( 

Sorry if this is in the wrong place.

---

### Post by Jagot on 2006-08-01
In Terminal, type:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by mysticrider92 on 2006-08-01
> **Jagot said:**
> In Terminal, type:

```
sudo gedit /etc/apt/sources.list
```

Thank you! :D

---

