---
title: "libGL.so.1 gets replaced"
date: 2006-08-13
forum: Desktop Environments
---

### Post by oedipuss on 2006-08-13
I after installing the nvidia drivers manually (not from the reps), they replaced the libGL.so.* links to point to the nvidia libGL. 
The mesa libGL file and package are also installed, but not used.

Still, each time a new package is installed, the link libGL.so.1 reverts to pointing to the mesa library (I think by ldconfig), regardless of the kind of the package. This disables direct rendering...

Currently, I manually replace the link each time, but I'd like to know why this happens, or if there's a way to fix it..

Thanks =)

---

