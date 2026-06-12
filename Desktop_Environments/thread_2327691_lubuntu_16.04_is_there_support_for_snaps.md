---
title: "lubuntu 16.04 is there support for snaps?"
date: 2016-06-13
forum: Desktop Environments
---

### Post by a.dusty.trail on 2016-06-13
Is snaps support standard in lubuntu 16.04 and if not can it be added manually?
If it can is there a guide?

---

### Post by vasa1 on 2016-06-13
> **a.dusty.trail said:**
> Is snaps support standard in lubuntu 16.04 and if not can it be added manually?
If it can is there a guide?Yes.

Please see [http://ubuntuforums.org/showthread.php?t=2321161&highlight=snap](http://ubuntuforums.org/showthread.php?t=2321161&highlight=snap)

---

### Post by grahammechanical on 2016-06-13
Snaps will install and work on Lubuntu but as Lubuntu is a small size (compared to Ubuntu) ISO image it does not come with a package called snapd by default. Ubuntu & Xubuntu have snapd by default. So, for Lubuntu the process is

```
sudo apt install snapd
```

Then to see what snaps are available in the snap channel run

```
snap find
```.

In this thread I show an image of the Krita snap installed on Ubuntu, Xubuntu & Lubuntu. Krtia is a KDE application. I wanted to add Kubuntu to this thread but I have twice failed to install Kubuntu 16.04 with the error message partman_commit failed exit code 1. 

[http://ubuntuforums.org/showthread.php?t=2327088](http://ubuntuforums.org/showthread.php?t=2327088)

Not all the apps in snap find are GUI apps. And some of them are experimental. But more are on the way.

Regards

---

