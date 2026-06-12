---
title: "compizconfig-python install error"
date: 2009-05-26
forum: Desktop Environments
---

### Post by Nycthbris on 2009-05-26
On a fresh Jaunty install I tried to install ccsm and got the following error:

```
jon@JMac:~$ sudo apt-get install compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compizconfig-settings-manager: Depends: python-compizconfig (>= 0.7.8) but it is not going to be installed
E: Broken packages

```

I did some digging and found this bug, related to the offending package (python-compizconfig):
[Bug #335728]("https://bugs.launchpad.net/ubuntu/+source/compizconfig-python/+bug/335728")

I'm getting the same errors described in the bug. It says a fix has been released but I can't seem to find it. Am I dumb or just blind?

**Edit:** Solved, I was using outdated repositories...

---

