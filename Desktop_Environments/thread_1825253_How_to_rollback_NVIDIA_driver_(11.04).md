---
title: "How to rollback NVIDIA driver (11.04)"
date: 2011-08-15
forum: Desktop Environments
---

### Post by &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081; on 2011-08-15
Hello!
I've used the 270'th version of NVIDIA driver with my GTS450 graphic card. After publishing the new 280 version of driver on NVIDIA resource, i've tried to install it manually. Installation was successfull, but when booting a conflict between versions was found(from kern.log) and only console mode is available. How can i rollback NVIDIA driver in console mode? Previous configuration of xorg.conf has been backuped.

Thank's.

---

### Post by &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081; on 2011-08-15
Will try to remove kernel module and install again.

---

### Post by Frogs Hair on 2011-08-15
You could run the purge command to remove the unwanted driver and then reinstall nvidia-current .
```
sudo apt-get --purge remove package name

```

To see a package list . 
```
 dpkg --list
```

To install Nvidia current , which is 270.41 .
```
sudo apt-get install nvidia-current
```

---

### Post by Duncan Williams on 2011-08-15
also if you want to re-install 280.
check this ppa > no manual messing about then...
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

280 from this ppa works fine on my system > 
Kernel		: Linux 2.6.38-10-generic (i686)

---

### Post by Bobhuber on 2011-08-15
> **&#1052 said:**
> Hello!
I've used the 270'th version of NVIDIA driver with my GTS450 graphic card. After publishing the new 280 version of driver on NVIDIA resource, i've tried to install it manually. Installation was successfull, but when booting a conflict between versions was found(from kern.log) and only console mode is available. How can i rollback NVIDIA driver in console mode? Previous configuration of xorg.conf has been backuped.

Thank's.

Follow the purge instructions and stick with the Nvidia current. I'm running (3) different op systems and have had nothing but problems with the new drivers with a GT430 card. The 270.41.06 has been very stable on all three systems. SUSE 11.04 gnome 3 - Unity - 10.10.

---

### Post by &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081; on 2011-08-16
Thank's all for help. Problem has been solved for now. I've removed nvidia-current package by apt-get --purge remove, then made changes in xorg.conf (insert 'nouveau' as default driver instead of 'nvidia'). These actions i've made under recovery console. After that i've booted on system and installed nvidia-current package. And finally i've replaced 'nouveau' by 'nvidia' in xorg.conf under recovery console. Then my 11.04 works ok.
I've also added repository by Duncan Williams to repositories, but now will not update (will not risk :)). Will do it later.

---

### Post by james19 on 2011-08-16
All efforts will be useless. You must re-install it.

---

### Post by Duncan Williams on 2011-08-17
It mentions to purge in the 280 x repo.
But I never did that. I just added repository to update manager and when it showed up in update manager, clicked install, rebooted after updates. All was good, also a bit faster than it was before for me on **high** quality settings.

(went from 270 to 280)

---

