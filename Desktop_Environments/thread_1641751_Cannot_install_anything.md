---
title: "Cannot install anything"
date: 2010-12-09
forum: Desktop Environments
---

### Post by Tehsimpl on 2010-12-09
Hey, sorry to bother you guys but I cannot install anything on my Ubuntu machine... I get this error if I do try and install something.

```
jacob@ubuntu:~$ apt-get install webhttrack
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libhttrack2 webhttrack-common
Suggested packages:
  httrack httrack-doc
The following NEW packages will be installed:
  libhttrack2 webhttrack webhttrack-common
0 upgraded, 3 newly installed, 0 to remove and 38 not upgraded.
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
jacob@ubuntu:~$ 

```

Help would be appreciated.

---

### Post by pricetech on 2010-12-09
Try renaming the lock file and see if that helps.

---

### Post by sikander3786 on 2010-12-09
I don't see 'sudo' there.

```
sudo apt-get install webhttrack
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

