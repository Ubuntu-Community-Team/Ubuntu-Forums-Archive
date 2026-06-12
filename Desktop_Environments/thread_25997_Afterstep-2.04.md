---
title: "Afterstep-2.04"
date: 2005-04-11
forum: Desktop Environments
---

### Post by hal8000 on 2005-04-11
A new version of afterstep has been released, but I cannot find a Debian build so have decided to compile from source. At the moment I have failures at the make stage, I believe these are related to X headers so will try and install the packages first and try again.

Meanwhile has anyone else got this installed successfully? Using Hoary 5.04; thanks in advance.

---

### Post by gil-galad on 2005-04-11
Try apt-get build-dep afterstep

---

### Post by hal8000 on 2005-04-11
Just tried the command :-

root@ubuntu:/home/anc # apt-get build-dep afterstep
Reading Package Lists... Done
Building Dependency Tree... Done
E: Unable to find a source package for afterstep

same message for afterstep-2.0 I already have afterstep 1.8 installed; looks like there is no build yet for Debian.

---

