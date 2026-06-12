---
title: "Why would a package be &quot;held back&quot;?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Joey French on 2005-11-27
I don't understand why this is:
```
joey@cpe-024-031-214-111:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  amule amule-utils linux-image-386 linux-image-k7
  linux-restricted-modules-386
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
joey@cpe-024-031-214-111:~$

```
What does it mean when a package is held back? Should I not upgrade them? 

Joey French

---

### Post by syklitengutt on 2005-11-27
Im just a noob, but I think it has something to do with
law in the us and restrictions.

If you go into the synaptics/settings/resporoties
press add and add the ones that are unselected.

---

### Post by [Rui] on 2005-11-27
It may be because it needs to add extra packages or remove some.

Do apt-get dist-bupgrade, instead.

---

### Post by syklitengutt on 2005-11-27
I think my answer was good...
(plz tell me it helped)
:)

---

### Post by astoltz on 2005-11-27
It just means that there are some other dependencies that are keeping those packages from being installed by themselves.  If you issue the command: ```
sudo apt-get dist-upgrade
``` it will try to resolve those auto-magically.  Or, if you do each package by itself, like ```
sudo apt-get install amule
``` it will mark all the dependencies for amule and give you the chance to accept or not.

---

### Post by Joey French on 2005-11-27
Okay. I guess that is a good enough explanation. I will give it a go.

---

### Post by Gustav on 2005-11-27
The usual reason for holding back packages when doing apt-get upgrade is that new packages need to be installed or old packages need to be removed. 

Apt-get with the upgrade option won't install new packages or remove old ones for that you need to use apt-get dist-upgrade.

There is no reason for not using apt-get dist-upgrade (it has nothing to do with moving to Dapper)

---

