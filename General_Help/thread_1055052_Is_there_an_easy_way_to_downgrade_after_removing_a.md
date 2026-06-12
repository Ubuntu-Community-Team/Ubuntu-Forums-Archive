---
title: "Is there an easy way to downgrade after removing a software source?"
date: 2009-01-30
forum: General Help
---

### Post by jis on 2009-01-30
I may add a software source such as backports or some third party software source that provides newer versions of packages installed from supported software sources. If I update such packages, is there an easy way to return to supported packages? I think it is not enough to remove the software source.

---

### Post by hyper_ch on 2009-01-30
remove and purge the installed software, remove the backport repo, try to reinstall the "lower" one,.

---

### Post by jis on 2009-01-30
I removed but I did not purge. So far so good. I had to use Synaptic to see which packages I have to remove; actually it was not accurate because it may show packages of many sources for one origin item, say ppa.launchpad.net/universe. Is there a command that would remove (or purge) software installed from certain source?

---

### Post by hyper_ch on 2009-01-30
you can have only one package installed through the package manager... so purging will deinstall that one

---

### Post by jis on 2009-01-30
> **hyper_ch said:**
> you can have only one package installed through the package manager... so purging will deinstall that one

What do you mean? Of course I can have many packages installed by the package manager. And I can purge several packages by
```
sudo apt-get purge pkg...
```
or
```
sudo apt-get autoremove --purge pkg...
```

---

