---
title: "Ktorrent not working, broken packages"
date: 2009-07-11
forum: Desktop Environments
---

### Post by kaustubh.bansal on 2009-07-11
I tried installing KTorrent using the following command, but there seems to be some problem.
```

kaustubh@ubuntu:~$ sudo apt-get install ktorrent
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ktorrent: Depends: kdebase-runtime (>= 4:4.2.1) but it is not going to be installed
            Depends: kdelibs5 (>= 4:4.2.1) but it is not going to be installed
            Depends: kdepimlibs5 (>= 4:4.2.2) but it is not going to be installed
            Depends: libqt4-svg (>= 4.5.0~+rc1) but it is not going to be installed
E: Broken packages


```

I also tried to install it using Synaptics Package manager but there also it has the same problem. 
I had installed KChmviewer some time ago, could it be the cause of the problem?

---

### Post by oldos2er on 2009-07-11
To fix broken packages, run **sudo apt-get install -f**.

 For the other problem, make sure all repositories are enabled (System, Administration, Software Sources).

---

