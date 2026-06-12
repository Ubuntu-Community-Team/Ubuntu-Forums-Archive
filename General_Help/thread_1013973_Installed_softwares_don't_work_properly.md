---
title: "Installed softwares don't work properly"
date: 2008-12-17
forum: General Help
---

### Post by roshanjose on 2008-12-17
When I install any software or any package..there is usually a list of dependencies..

the dependencies which are also packages are the latest version of that  particular package..

the problem is that the other version of the same package is required for the proper working of the installed software...

An Example can illustrate this better:

Say i install software X....

it requires gcc-4.2.....so it selects this version...but for this to be totally functional gcc is also required.. but the software X does not specify gcc....

such problems did occur for some package i dont remember at someone's system...

how can we make sure that all required are installed

---

### Post by taurus on 2008-12-17
Install programs from the repos and all the dependencies will be taken care off.  Install something outside of repos will require you to hunt down all the dependencies or upgrade to the latest ones which could cause trouble for your machine.

---

### Post by roshanjose on 2008-12-17
hey i install from the repos only

---

### Post by taurus on 2008-12-17
What program that you are trying to install that fails the dependencies test?

```
sudo apt-get update
sudo apt-get install *program_name*
```

---

### Post by cdenley on 2008-12-17
You refer to two seperate packages: gcc and gcc-4.2. The package gcc is a small package which depends on the latest gcc (gcc-4.3 in intrepid). You can install gcc, gcc-4.2, and gcc-4.3, and have all your dependencies resolved. If you have a dependency conflict, file a bug report. There shouldn't be any dependency conflicts in the ubuntu repositories. If there are, see if there is a bug report, and if not, create one.

---

### Post by roshanjose on 2008-12-18
kk thanq

---

