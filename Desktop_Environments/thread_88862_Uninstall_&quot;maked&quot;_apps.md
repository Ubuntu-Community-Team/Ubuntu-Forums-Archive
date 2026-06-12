---
title: "Uninstall &quot;maked&quot; apps"
date: 2005-11-11
forum: Desktop Environments
---

### Post by kurokikaze on 2005-11-11
Hi, I've installed several apps by their sources using the make and make install procedure. Now I'd like to get rid of some of this apps. Obviously there is no way of doing this through synaptic. How can I simply and fast erase the files installed by this applications?

Thanks a lot

---

### Post by Remmelas on 2005-11-11
if you still have the apps make file, some provide uninstall routines by doing make uninstall
in the future, you can use 'checkinstall' in place of make install(you have to install checkinstall first by doing sudo apt-get install checkinstall), and it will package it, and install it, so that when you want to remove such things you can just select it for removal in synaptic.

---

### Post by kurokikaze on 2005-11-14
Thanks for your help. I guess "checkinstall" is exaclty what i was looking for.

---

