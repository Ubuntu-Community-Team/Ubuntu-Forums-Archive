---
title: "Restore deleted /etc/ file to default"
date: 2009-01-16
forum: General Help
---

### Post by voidvector on 2009-01-16
Sometimes ago, I manually deleted some files and folders in /etc for applications that I had uninstalled. 

However, now I have need for those applications again. After I re-installed them, the applications fail to start because the re-installation doesn't try to install a new copy of those configuration files (even though they are missing). 

How do I force a full installation?

---

### Post by blazemore on 2009-01-16
```
sudo aptitude purge **packagename**
```
will remove the program and totally remove all configuration files.

```
sudo aptitude install **packagename**
```
will reinstall the application, re-creating the default settings somewhere under /etc.

---

### Post by hikaricore on 2009-01-16
Be careful using **aptitude**!
Be sure you know what packages you will be adding or removing before saying yes or you can muck a few things up.

When in doubt use apt-get as such:

> sudo apt-get remove --purge **packagename**
sudo apt-get install **packagename**

---

### Post by dcstar on 2009-01-16
> **hikaricore said:**
> Be careful using **aptitude**!
Be sure you know what packages you will be adding or removing before saying yes or you can muck a few things up.

When in doubt use apt-get as such:

Aptitude is just a front-end for apt (as is Synaptic), I can't see how using the lower-level command structure is any safer - in fact it gives you more opportunity to break things.

---

### Post by blazemore on 2009-01-16
hikaricore I don't think you are right.

Aptitude and Apt-get both are just command-line tools for using the Advanced Packaging Tool (apt).

I know the purge command works in aptitude and I wasn't sure about apt-get, so that's why I included it here.

They both have the potential to do serious damage if you accidently uninstall the wrong thing.
The only differences are:

* Slight differences in command names (full-upgrade vs dist-upgrade)
* Aptitude has a search function
* apt-get supports wildcards

---

### Post by hikaricore on 2009-01-16
> **dcstar said:**
> Aptitude is just a front-end for apt (as is Synaptic), I can't see how using the lower-level command structure is any safer - in fact it gives you more opportunity to break things.

I can't tell if you're saying I'm right or not... your message is confusing.

We discourage the use of aptitude in many situations and this will not change.
When in doubt apt-get is safer and won't take more drastic actions that aptitude sometimes will.

---

### Post by blazemore on 2009-01-16
Does apt-get support Purge? If it does I'll gladly edit my original post as I'm aware of the problems that can arise through improper use of Aptitude.

---

