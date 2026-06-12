---
title: "pcsx2 install problems"
date: 2015-12-04
forum: Emulators
---

### Post by oldmacaroni on 2015-12-04
Hey, 
I'm having an extremely similar problem to this thread- [http://ubuntuforums.org/showthread.php?t=230267]("http://ubuntuforums.org/showthread.php?t=2302676") when trying to install pcsx2 (I am also running 64 bit 14.04). 
I installed the official ppa, all went well, but when I try apt-get install pcsx2 I get this 
```
 The following packages have unmet dependencies:
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages. 
```

I tried apt-get update, apt-get upgrade and apt-get dist-upgrade in this order and everything went well once again, but I still receive this error message when trying to install. I tried apt-get install libcheese-gtk23 libcheese7, it worked but I already had the newest versions (why is a webcam tool a dependency for an emulator anyway?). I tried to install pcsx2 again but got the same error. When trying to install with synaptic it wants me to remove 20+ packages so I didn't go through with that. 

Any ideas? thanks

---

