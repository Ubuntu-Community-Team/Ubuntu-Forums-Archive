---
title: "Cannot mount new volumes with thunar-volman installed."
date: 2009-09-03
forum: Desktop Environments
---

### Post by dE_logics on 2009-09-03
After finally installing thunar volman from source, I cannot mount new volumes even with mount...it says the device is not found in m or fstab...same old issue.

I installed xfce from source...so all xfce specific packages HAVE to be installed from source.

I have the following processes running - 

gvfs-gphoto2-volume-monitor
gvfs-hal-volume-monitor

---

### Post by dE_logics on 2009-09-03
We got a translation to the above?

---

### Post by dE_logics on 2009-09-03
Issue resolved.

How to install xfce from source - 

1)After unpacking the downloaded xfce archive, in the extracted folder, extract the individual archives which will be there.

2)Go in each folder and compile each package in the right order so as to resolve all dependencies (they are dependent on each other)...however if you do not find the dependency in the main folder itself, you have to install it from the repos.

3)**To enable automatic mounting of volumes**, download thunar-volman from goodies.xfce.org and compile it.

4)recompile the 'thunar' package as you did in step 2...and you'll be done.

---

